---
title: Prolog 4 - Inference Engine of Prolog - Resolution and Tree Search
tags: [Notebooks/Cmput 325]
created: '2019-03-27T02:09:07.579Z'
modified: '2019-03-27T02:34:27.026Z'
favorited: true
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

