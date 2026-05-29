# Understanding Bayesian Networks

## Overview

This project explores Bayesian Networks (BNs), which are probabilistic graphical models used to represent uncertainty and perform reasoning based on probabilities.

Bayesian Networks help AI systems make decisions when information is incomplete or uncertain. They are widely used in areas such as medical diagnosis, recommendation systems, risk analysis, and prediction problems.

In this project, a simple Bayesian Network is implemented to model student academic performance and demonstrate probabilistic inference.

---

# Project Structure

## Exam.py

This file contains the Bayesian Network implementation.

The program models relationships between different variables and performs probabilistic inference based on observed evidence.

The network is built using:

- Random variables
- Conditional probability tables (CPTs)
- Bayesian inference calculations

The implementation demonstrates how probabilities can be updated when new information becomes available.

---

# Core Concepts

## Random Variables

A Bayesian Network consists of random variables represented as nodes.

Examples:

- Difficulty of a course
- Student intelligence
- Grade obtained
- SAT score
- Recommendation letter

Each variable can have different possible values.

---

## Directed Graph

Bayesian Networks are represented using a Directed Acyclic Graph (DAG).

In the graph:

- Nodes represent variables.
- Arrows represent dependencies.

Example:

```text
Difficulty → Grade
Intelligence → Grade
Intelligence → SAT
Grade → Letter
```

The arrows show which variables directly influence others.

---

## Conditional Probability Tables (CPTs)

Each node stores probabilities that describe how it depends on its parent nodes.

Examples:

```text
P(Intelligence = High)
P(Grade | Intelligence, Difficulty)
P(SAT | Intelligence)
P(Letter | Grade)
```

These probabilities form the knowledge base of the network.

---

## Joint Probability

A Bayesian Network represents the joint probability distribution of all variables.

Instead of storing one large probability table, the network breaks it into smaller conditional probability tables.

This makes reasoning more efficient.

---

## Inference

Inference is the process of calculating the probability of an event given some evidence.

Example:

```text
What is the probability that a student has high intelligence
if they received a weak recommendation letter?
```

The network uses existing probabilities to compute the answer.

---

# Tools for Building Bayesian Networks

## Pure Python

Bayesian Networks can be implemented using standard Python data structures.

Advantages:

- Easy to understand
- No external dependencies
- Suitable for assignments and learning

Best for:

- Small Bayesian Networks
- Educational projects
- Demonstrating inference concepts

---

## pgmpy

pgmpy is a popular Python library for Bayesian Networks.

Features:

- Bayesian Network creation
- Conditional probability tables
- Exact inference
- Approximate inference
- Learning from data

Installation:

```bash
pip install pgmpy
```

---

## bnlearn

bnlearn is used for learning Bayesian Network structures from datasets.

Features:

- Structure learning
- Probability estimation
- Visualization

Best for:

- Data-driven Bayesian Networks
- Research applications

Installation:

```bash
pip install bnlearn
```

---

# Inference Methods

## Exact Inference

Exact inference calculates the precise probability of a query.

Examples:

- Enumeration
- Variable Elimination

Advantages:

- Accurate results

Limitations:

- Computationally expensive for large networks

---

## Approximate Inference

Approximate inference uses sampling techniques.

Examples:

- Rejection Sampling
- Likelihood Weighting
- Gibbs Sampling

Advantages:

- Faster for large networks

Limitations:

- Results are approximate

---

# Example Used in This Project

The Bayesian Network models student academic performance.

Variables:

- Difficulty (High / Low)
- Intelligence (High / Low)
- Grade (A / B / C)
- SAT Score (High / Low)
- Recommendation Letter (Strong / Weak)

Relationships:

```text
Difficulty → Grade
Intelligence → Grade
Intelligence → SAT
Grade → Letter
```

The model can answer questions such as:

```text
What is the probability that a student has high intelligence
given a weak recommendation letter and a difficult course?
```

The answer is calculated using Bayesian inference.

---

# Features

- Bayesian Network representation
- Directed Acyclic Graph structure
- Conditional Probability Tables
- Probabilistic reasoning
- Exact inference
- Student performance prediction example
- Pure Python implementation

---

# How the System Works

1. Variables are defined as nodes.
2. Dependencies are represented using directed edges.
3. Conditional probability tables are created.
4. Evidence is provided to the network.
5. Bayesian inference is performed.
6. Posterior probabilities are calculated and displayed.

---

# Running the Project

Run the program:

```bash
python Exam.py
```

or

```bash
python BN/Exam.py
```

depending on your folder structure.

---

# Conclusion

This project demonstrates how Bayesian Networks can be used to model uncertainty and perform probabilistic reasoning.

By representing variables and their dependencies as a graph, the system can infer new information from existing evidence and answer probability-based queries.

The example of student academic performance shows how Bayesian Networks can be applied to real-world decision-making problems where uncertainty is present.
