# Adversarial Game Search Algorithms

## Overview

This project implements four AI search algorithms used for decision-making in two-player games:

1. Minimax Search
2. Alpha-Beta Pruning
3. Heuristic Alpha-Beta Search
4. Monte-Carlo Tree Search (MCTS)

These algorithms are tested using two classic games:

- Tic-Tac-Toe
- Connect Four

The objective is to compare different approaches for finding the best move in a game while balancing accuracy and efficiency.

---

# Project Structure

## game.py

This file contains the game logic.

Responsibilities:

- Board representation
- Legal move generation
- Applying moves
- Win detection
- Draw detection
- Terminal state checking

Games implemented:

- Tic-Tac-Toe
- Connect Four

---

## search.py

This file contains implementations of all search algorithms.

Implemented algorithms:

- Minimax
- Alpha-Beta Pruning
- Heuristic Alpha-Beta
- Monte-Carlo Tree Search (MCTS)

The algorithms use the game states provided by `game.py` to determine the best move.

---

## testcases.py

This file contains test cases used to verify:

- Correct game mechanics
- Win detection
- Draw detection
- Search algorithm correctness
- Offensive move selection
- Defensive move selection

---

# Algorithms Implemented

## 1. Minimax Search

Minimax is a decision-making algorithm for two-player zero-sum games.

The idea is:

- MAX player tries to maximize the score.
- MIN player tries to minimize the score.

The algorithm explores all possible future moves and chooses the optimal one.

### Advantages

- Guarantees optimal play.
- Easy to understand.

### Limitations

- Slow for large game trees.
- Explores many unnecessary states.

---

## 2. Alpha-Beta Pruning

Alpha-Beta is an optimized version of Minimax.

It avoids exploring branches that cannot affect the final decision.

### Advantages

- Returns the same result as Minimax.
- Searches fewer states.
- Faster execution.

---

## 3. Heuristic Alpha-Beta Search

For larger games like Connect Four, searching the complete game tree is impractical.

This approach:

- Limits search depth.
- Uses a heuristic evaluation function to estimate board quality.

The evaluation function rewards:

- Winning opportunities
- Good board positions
- Blocking opponent threats

### Advantages

- Much faster than full search.
- Suitable for larger games.

---

## 4. Monte-Carlo Tree Search (MCTS)

MCTS chooses moves using repeated simulations.

The algorithm repeatedly:

1. Selects a promising node.
2. Expands the tree.
3. Simulates a random game.
4. Updates statistics.

The move with the best simulation results is selected.

### Advantages

- Does not require a handcrafted evaluation function.
- Works well in large search spaces.

---

# Features

- Full Minimax implementation
- Alpha-Beta optimization
- Heuristic search support
- Monte-Carlo Tree Search
- Tic-Tac-Toe support
- Connect Four support
- Interactive gameplay
- Automated testing

---

# How the System Works

1. The game state is initialized.
2. Legal moves are generated.
3. The selected search algorithm evaluates possible moves.
4. The best move is chosen.
5. The game state is updated.
6. The process repeats until the game ends.

---

# Test Cases and Correctness Verification

The following test cases were used to verify the correctness of the implementation.

## Tic-Tac-Toe Test Cases

### Test Case 1: Initial State Validation

**Objective:**
Verify that a new game starts correctly.

**Checks:**

- Board contains 9 empty cells.
- Player X starts first.
- State is non-terminal.
- 9 legal moves exist.

**Expected Result:**
All conditions hold.

---

### Test Case 2: Win Detection

**Board:**

```text
X X X
O O .
. . .
```

**Checks:**

- State is terminal.
- Winner is X.

**Expected Result:**
Win detected correctly.

---

### Test Case 3: Draw Detection

**Board:**

```text
X O X
X O O
O X X
```

**Checks:**

- Board full.
- No winner.
- State is terminal.

**Expected Result:**
Draw detected correctly.

---

### Test Case 4: Immediate Winning Move

**Board:**

```text
X X .
O O .
. . .
```

**Expected Move:**
Cell 2

**Algorithms Tested:**

- Minimax
- Alpha-Beta
- Heuristic Alpha-Beta
- MCTS

**Expected Result:**
Winning move selected.

---

### Test Case 5: Defensive Blocking

**Board:**

```text
O O .
X . .
. X .
```

**Expected Move:**
Cell 2

**Algorithms Tested:**

- Minimax
- Alpha-Beta
- Heuristic Alpha-Beta
- MCTS

**Expected Result:**
Blocking move selected.

---

## Connect Four Test Cases

### Test Case 6: Piece Drop Physics

**Objective:**
Verify gravity mechanics.

**Checks:**

- Piece falls to lowest available position.
- Turn changes correctly.

**Expected Result:**
Correct piece placement.

---

### Test Case 7: Horizontal Win Detection

**Configuration:**

```text
X X X X
```

on the same row.

**Expected Result:**
Win detected.

---

### Test Case 8: Vertical Win Detection

**Configuration:**

```text
X
X
X
X
```

in the same column.

**Expected Result:**
Win detected.

---

### Test Case 9: Immediate Winning Move

**Objective:**
Verify that algorithms choose a winning move.

**Algorithms Tested:**

- Heuristic Alpha-Beta
- MCTS

**Expected Result:**
Winning column selected.

---

### Test Case 10: Defensive Blocking

**Objective:**
Verify that algorithms block an opponent's winning move.

**Algorithms Tested:**

- Heuristic Alpha-Beta
- MCTS

**Expected Result:**
Threat is blocked.

---

# Test Summary

| Category | Number of Tests |
|-----------|----------------|
| Tic-Tac-Toe | 5 |
| Connect Four | 5 |
| Total | 10 |

The tests verify:

- Game mechanics
- Legal move generation
- Win detection
- Draw detection
- Terminal state recognition
- Correct search decisions
- Offensive play
- Defensive play

---

# Running the Project

Run all tests:

```bash
python testcases.py
```

or

```bash
python Search_Algos/testcases.py
```

Run interactive mode:

```bash
python testcases.py play
```

---

# Conclusion

This project demonstrates the implementation of four important AI search algorithms used in adversarial games.

The results show that:

- Minimax provides optimal decisions but is computationally expensive.
- Alpha-Beta significantly reduces unnecessary search.
- Heuristic Alpha-Beta makes larger games manageable.
- MCTS provides a flexible simulation-based approach for decision making.

Together, these algorithms demonstrate different techniques for solving game-playing problems in Artificial Intelligence.
