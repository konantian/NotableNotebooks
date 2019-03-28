---
title: Prolog 4 - Inference Engine of Prolog - Resolution and Tree Search
tags: [Notebooks/Cmput 325]
created: '2019-03-27T02:09:07.579Z'
modified: '2019-03-27T03:14:33.493Z'
---

# Prolog 4 - Inference Engine of Prolog - Resolution and Tree Search

### Horn Clause
  * A single atom at the head
  * Prolog uses only Horn clauses

### Variables
  * Variables in facts and rules are universally quantified
  * Variables in queries are existentially quantified

### Resolution
  * Take two clauses c1 and c2 that are disjunctions of literals. One contains a variable and the other contains 
the same variable but negated, ~V
  * Resolution is just disjunction of everything in c1 and c2, except v and ~v dropped.
  * Example:
    c1 = ~a v b, c2 = a v c
    Resolution of c1 and c2: b v c

### Derived Goal,Resolution for Prolog
  * In logic, can select any subgoal $C_i$ to resolve first
  * In Prolog, fix the selection rule to be the leftmore, $C_1$

### Prolog Tree Search
  * Tree represents the Prolog search process
  * Root of tree: original query
  * Child of a node: a derived goal created by resolution
  * A node can have several different children
  * Each child represents a resolution with a different clause in the program
  * A **derivation** is a sequence of resolution steps
  * The tree contains all possible derivations for a given program and a given goal
  * Leaf node in the tree:
    1. Leaf node is an empty goal - success!
    2. Leaf node of a failed branch, first subgoal is not unifiable with the head of any clause in program
