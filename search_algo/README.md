# Adversarial Game Search Algorithms

## AI Assignment 4: Minimax, Alpha-Beta, Heuristic Search, and MCTS

### Objective

The objective of this assignment is to implement and compare four adversarial search algorithms used in two-player zero-sum games:

1. Minimax Search
2. Alpha-Beta Pruning
3. Heuristic Alpha-Beta Search
4. Monte-Carlo Tree Search (MCTS)

These algorithms are evaluated on the following games:

- Tic-Tac-Toe (3×3)
- Connect Four (6×7)

---

# Algorithms Implemented

## 1. Minimax Search

Minimax is a classical adversarial search algorithm for two-player zero-sum games.

The algorithm assumes:

- MAX attempts to maximize the utility.
- MIN attempts to minimize the utility.

At each state:

- If the state is terminal, return its utility.
- MAX chooses the action with the highest value.
- MIN chooses the action with the lowest value.

### Advantages

- Guarantees optimal play.
- Complete for finite game trees.

### Limitations

- Computationally expensive.
- Time complexity grows exponentially.

### Complexity

```text
Time: O(b^d)
Space: O(d)
```

where:

- b = branching factor
- d = depth of game tree

---

## 2. Alpha-Beta Pruning

Alpha-Beta pruning is an optimization of Minimax.

It eliminates branches that cannot affect the final decision while still returning the same optimal move as Minimax.

### Definitions

- α (Alpha): Best value MAX can guarantee.
- β (Beta): Best value MIN can guarantee.

Pruning occurs whenever:

```text
α ≥ β
```

### Advantages

- Produces the same result as Minimax.
- Explores significantly fewer nodes.
- Faster in practice.

### Complexity

Worst Case:

```text
O(b^d)
```

Best Case:

```text
O(b^(d/2))
```

---

## 3. Heuristic Alpha-Beta Search

For larger games such as Connect Four, searching the entire game tree is impractical.

The solution is to:

1. Limit search depth.
2. Use a heuristic evaluation function.

### Move Ordering

Move ordering improves pruning efficiency.

#### Tic-Tac-Toe

Priority:

1. Center
2. Corners
3. Edges

#### Connect Four

Priority:

- Center columns first
- Then outward columns

### Evaluation Function

#### Tic-Tac-Toe

| Pattern | Score |
|----------|--------|
| 3 player pieces | +100000 |
| 2 player + 1 empty | +10 |
| 1 player + 2 empty | +1 |
| 3 opponent pieces | -100000 |
| 2 opponent + 1 empty | -10 |
| 1 opponent + 2 empty | -1 |

#### Connect Four

| Pattern | Score |
|----------|--------|
| 3 player + 1 empty | +50 |
| 2 player + 2 empty | +10 |
| 3 opponent + 1 empty | -100 |
| 2 opponent + 2 empty | -10 |
| Center column piece | +4 |

### Advantages

- Much faster than full Minimax.
- Suitable for larger game spaces.
- Provides strong practical performance.

---

## 4. Monte-Carlo Tree Search (MCTS)

MCTS builds a search tree dynamically using random simulations.

Unlike Alpha-Beta, it does not require a handcrafted heuristic.

### Four Phases

#### 1. Selection

Choose the most promising child using:

```text
UCT = Q/N + C * sqrt(ln(parent_visits)/N)
```

where:

- Q = total reward
- N = visit count
- C = exploration constant

#### 2. Expansion

Expand a previously unexplored node.

#### 3. Simulation

Play random moves until a terminal state is reached.

#### 4. Backpropagation

Update statistics from the simulation result back to the root.

### Advantages

- Works well for large state spaces.
- Requires little domain knowledge.
- Balances exploration and exploitation automatically.

---

# Project Structure

## game.py

Contains game implementations and state management.

Responsibilities:

- State representation
- Legal move generation
- State transitions
- Win detection
- Draw detection

Games implemented:

- TicTacToeState
- ConnectFourState

---

## search.py

Contains implementations of:

- Minimax Search
- Alpha-Beta Search
- Heuristic Alpha-Beta Search
- Monte-Carlo Tree Search

---

## testcases.py

Contains automated test cases for:

- Game mechanics
- Terminal state detection
- Search algorithm correctness
- Offensive and defensive move selection

---

# Test Cases and Correctness Verification

To verify correctness, a comprehensive set of test cases was designed for both games.

## Tic-Tac-Toe Test Cases

### Test Case 1: Initial State Validation

**Objective:** Verify that a newly initialized board is valid.

**Checks:**
- Board contains 9 empty cells.
- Player X starts first.
- State is not terminal.
- Exactly 9 legal moves exist.

**Expected Result:** All conditions hold.

---

### Test Case 2: Win Detection

**Objective:** Verify correct detection of a winning state.

**Board:**

```text
X X X
O O .
. . .
```

**Checks:**
- State is terminal.
- Winner is X.
- Utility value corresponds to a win.

**Expected Result:** Win detected correctly.

---

### Test Case 3: Draw Detection

**Objective:** Verify correct detection of draw states.

**Board:**

```text
X O X
X O O
O X X
```

**Checks:**
- Board is full.
- No winner exists.
- State is terminal.

**Expected Result:** Draw detected correctly.

---

### Test Case 4: Immediate Winning Move

**Objective:** Verify that algorithms select an available winning move.

**Board:**

```text
X X .
O O .
. . .
```

**Expected Move:** Cell 2

**Algorithms Tested:**
- Minimax
- Alpha-Beta
- Heuristic Alpha-Beta
- MCTS

**Expected Result:** Winning move selected.

---

### Test Case 5: Defensive Blocking

**Objective:** Verify that algorithms block an opponent's immediate win.

**Board:**

```text
O O .
X . .
. X .
```

**Expected Move:** Cell 2

**Algorithms Tested:**
- Minimax
- Alpha-Beta
- Heuristic Alpha-Beta
- MCTS

**Expected Result:** Blocking move selected.

---

## Connect Four Test Cases

### Test Case 6: Piece Drop Physics

**Objective:** Verify gravity mechanics.

**Procedure:**
- Drop a piece into an empty column.

**Checks:**
- Piece lands in the lowest available position.
- Turn changes correctly.

**Expected Result:** Correct piece placement.

---

### Test Case 7: Horizontal Win Detection

**Objective:** Verify horizontal four-in-a-row detection.

**Configuration:**

```text
X X X X
```

on the same row.

**Expected Result:** Win detected.

---

### Test Case 8: Vertical Win Detection

**Objective:** Verify vertical four-in-a-row detection.

**Configuration:**

```text
X
X
X
X
```

in the same column.

**Expected Result:** Win detected.

---

### Test Case 9: Immediate Winning Move

**Objective:** Verify that algorithms select a direct winning move.

**Configuration:**
- Three connected pieces already exist.
- One move completes four-in-a-row.

**Algorithms Tested:**
- Heuristic Alpha-Beta
- MCTS

**Expected Result:** Winning column selected.

---

### Test Case 10: Defensive Blocking

**Objective:** Verify that algorithms block an opponent's winning threat.

**Configuration:**
- Opponent has three connected pieces.
- One move remains for victory.

**Algorithms Tested:**
- Heuristic Alpha-Beta
- MCTS

**Expected Result:** Threat is blocked.

---

# Test Summary

| Category | Number of Tests |
|-----------|----------------|
| Tic-Tac-Toe | 5 |
| Connect Four | 5 |
| Total | 10 |

The test suite verifies:

- Correct game mechanics
- Legal move generation
- Win detection
- Draw detection
- Terminal state recognition
- Optimal move selection
- Defensive move selection
- Correctness of all implemented search algorithms

---

# Running the Project

## Run All Tests

```bash
python testcases.py
```

or

```bash
python Search_Algos/testcases.py
```

## Run Specific Test Groups

Tic-Tac-Toe only:

```bash
python testcases.py ttt
```

Connect Four only:

```bash
python testcases.py c4
```

## Run Interactive Mode

```bash
python testcases.py play
```

The user can:

- Play Tic-Tac-Toe or Connect Four.
- Choose turn order.
- Select Minimax, Alpha-Beta, Heuristic Alpha-Beta, or MCTS as the AI opponent.

---

# Conclusion

This assignment successfully implements four important adversarial search algorithms and evaluates them on Tic-Tac-Toe and Connect Four.

The results demonstrate that:

- Minimax guarantees optimal play but is computationally expensive.
- Alpha-Beta significantly reduces the search space while preserving optimality.
- Heuristic Alpha-Beta enables efficient play in larger games through depth-limited search and evaluation functions.
- MCTS provides a flexible simulation-based approach that performs effectively without handcrafted heuristics.

Together, these algorithms illustrate different strategies for decision-making in adversarial environments and highlight the trade-offs between optimality, efficiency, and scalability.
