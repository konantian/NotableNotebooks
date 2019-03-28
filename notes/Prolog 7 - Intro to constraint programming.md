---
title: Prolog 7 - Intro to constraint programming
tags: [Notebooks/Cmput 325]
created: '2019-03-28T17:39:53.525Z'
modified: '2019-03-28T20:44:21.888Z'
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
  * Applications
    * Many real world problems can be translated into a SAT problem
    * If we can solve SAT efficiently we immediately have an efficient solver for all of these real world problems. 

### Constraint Satisfaction Problem(CSP)
  * A constraint satisfaction problem (CSP) is a formalization of a constraint satisfaction problem
  * A CSP consists of three parts
    1. A set of variables $X = x_1, .... X_n$
    2. A domain $D_i$ for each variable $x_i$: a finite set of possible values for this variable
    3. A set of constraints restricting the values that the variables can simultaneously take

### Solution to a CSP
  * Find any one solution
  * Find all solutions
  * Find an optimal, or at least good solution, given an objective function defined in terms of some or all of the variables

### Constraint Solving Methods
  * Many constraints are local - involve a small number of variables
  * A solution to all constraints is global - involves all variables

### Consistency techniques
  * **Consistency techniques** remove values from domains which are **inconsistent** with the variable assignments
  * Remove values from domains is temporary
  * It depends on the other variable assignments done
  * Node Consistency
    * Given a constraint with only **one** unassigned variable
    * Remove all values from domain which constradict this constraint
  * Arc Consistnecy
    * Arc consistency applies to a constraint with two unassigned variables
    * This is done repeatedly for all variables until no further domain reduction is possible
    * The final CSP with reduced domains is called arc consistent
    

  

