# AI Assignment 5

1. **Search Algorithms**: Implementing AI players for Tic-Tac-Toe and Connect Four using Minimax, Alpha-Beta Pruning, and Monte-Carlo Tree Search (MCTS).
2. **Travel Planner**: A smart daily trip planner that recommends places, pairs food with beverages, and optimizes budget.
3. **Knowledge Graphs (KG)**: Storing facts as Subject-Predicate-Object triples and searching for connections.
4. **Bayesian Networks (BN)**: Modeling dependencies and calculating probabilities of different outcomes.

---
## 1: Adversarial Game Search Algorithms

This directory implements four major AI algorithms for two-player, turn-based games:
1. **Minimax**: Searches all moves to play perfectly.
2. **Alpha-Beta Pruning**: An optimized Minimax that ignores bad moves to search faster.
3. **Heuristic Alpha-Beta**: Cuts off the search at a set depth and guesses who is winning using a board evaluator.
4. **Monte-Carlo Tree Search (MCTS)**: Runs random play simulations to make decisions without needing a custom board evaluator.

### 1. Games Supported
* **Tic-Tac-Toe**: Fully solved by Minimax and Alpha-Beta.
* **Connect Four**: Solved using Heuristic Alpha-Beta (with move ordering to search center columns first) and MCTS.

### 2. How to Run the Code

#### Run Tests
Runs the test suite to verify the AI blocks wins and takes immediate wins:
```bash
python testcasess.py
```

#### Play Against the AI
Play Tic-Tac-Toe or Connect Four against any of the search algorithms directly in your terminal:
```bash
python testcasess.py play
```
You can choose to go first or second and pick the AI search algorithm you want to face!

---

## 2: Semantically Paired Travel Planner

This is a complete **AI Travel Planner** that builds custom daily trip dossiers.

### 1. Code Architecture
* `wine.py`: Stores beverages, regional production, and food pairing axioms.
* `places_db.py`: Database of activities in Kyoto, Napa Valley, Tuscany, and Paris.
* `food.py`: Recommends local foods based on user dietary restrictions (Vegetarian, Vegan, Gluten-Free) and pairs them with drinks.
* `planner.py`: Ranks tourist spots using a custom scoring system and schedules morning and afternoon slots.
* `cost.py`: Tracks trip costs. If the trip is over budget, it replaces expensive spots with cheaper/free alternatives in the same region until it is under budget.
* `travel.py`: The entry point script.

### 2. How to Run the Code

#### Direct Command Arguments
Provide your choices directly in the command:
```bash
# Format: python travel_planner.py [Destination] [Days] [Style] [Budget] [Diet] [Alcohol] [Interests]
python travel.py Kyoto 3 moderate 600 none yes Culture,Foodie
```

#### Interactive Questionnaire Mode
Run the script with no arguments to answer simple questions in the terminal:
```bash
python travel.py
```
The program will generate a detailed daily trip plan showing planned activities, paired dining suggestions, and a breakdown of costs.

---

## 3: Knowledge Graphs (KG)

A **Knowledge Graph** (KG) is a way to represent real-world information as a network of entities and relationships.

### 1. Core Ideas
* **Triples**: Information is stored in a three-part format: `(Subject) -[Relationship]-> (Object)`. For example: `(Kyoto) -[offers_dish]-> (Buddhist Kaiseki)`.
* **Ontology**: The rules and categories of the graph.
* **Traversal**: Finding paths between two concepts by following the arrows.

### 2. How to Run the Code
We have two versions of the knowledge graph:

#### A. Pure Python Graph (`simple_kg.py`)
No extra installations needed. Runs instantly.
```bash
python simple.py
```
* **What it does**: Stores facts in simple dictionary lists and uses a custom Depth-First Search (DFS) to find paths between cities and foods.

#### B. NetworkX Graph (`networkx_kg.py`)
Uses the `networkx` library to build and analyze a graph.
```bash
python network.py
```
* **What it does**: Checks connections and finds the shortest path between items using built-in graph algorithms.
*(Note: Run `pip install networkx` inside venv first if you don't have it).*

---

## 4: Bayesian Networks (BN)

A **Bayesian Network** (BN) is a graph that shows how different events depend on each other. It uses nodes (variables) and arrows (dependencies) to calculate probabilities when we only have partial information.

### 1. Core Ideas
* **Nodes**: Represent variables (like course difficulty, intelligence, grade).
* **Arrows**: Show direct influence. If $A \rightarrow B$, then $A$ directly influences $B$.
* **Probability Tables (CPTs)**: Each node has a table showing the probability of each outcome based on its parents.

### 2. Solving Probabilities (Inference)
* **Exact Inference (Enumeration)**: Calculates precise probabilities by adding up all possible scenarios. Simple to write but gets slow on large graphs.
* **Approximate Inference (Sampling)**: Runs random simulations to estimate probabilities when the graph is too big to solve exactly.

### 3. How to Run the Code
We modeled a student admissions network (difficulty, intelligence, grade, SAT score, letter of recommendation).

You can run the script to see the probability calculator in action:
```bash
# Move to the BN folder and run:
python simple.py
```
* **Example Query**: If a student gets a weak recommendation letter from a highly difficult class, what is the probability that the student has high intelligence?
* **Output**: The script calculates this exact value and displays the math steps in the console.
