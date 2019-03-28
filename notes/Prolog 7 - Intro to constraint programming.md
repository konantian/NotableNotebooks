---
title: Prolog 7 - Intro to constraint programming
tags: [Notebooks/Cmput 325]
created: '2019-03-28T17:39:53.525Z'
modified: '2019-03-28T19:32:38.506Z'
---

# Prolog 7 - Intro to constraint programming

### Constraing programming
  * The study of computatonal models and systems based on constraints
  * Idea: Model and solve a problem by exploring the constraints that can fully characterize the problem
  * Any solution of the problem must satisfy all stated constraints.

### Satisfiability Checking(SAT)
  * SAT is a fundamental but difficult problem in computing science.
  * Given a formula with boolean variables and decide whether the formula is satisfiable
  * Notation
    * A boolean variable $x_i$ can have values true(1) or false(0)
    * A single clause is satisfied iff it contains at least one literal that is true in the assignment
    * A set of clauses is satisfied by an assignment iff each clause satisfied
  * Example
    Variables $x_1$ $x_2$ $x_3$ $x_4$
    Assignment a: $x_1$ = 1 $x_2$ = 0 $x_3$ = 0 $x_4$ = 1
    Clause c: ~$x_1$ v $x_2$ v ~ $x_3$ v ~$x_4$
    c is satisfied by __a__ because $x_3$ = 0 means ~ $x_3$ = 1 
