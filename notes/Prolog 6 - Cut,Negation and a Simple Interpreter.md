---
title: 'Prolog 6 - Cut,Negation and a Simple Interpreter'
tags: [Notebooks/Cmput 325]
created: '2019-03-28T01:04:30.390Z'
modified: '2019-03-28T02:37:11.505Z'
---

# Prolog 6 - Cut,Negation and a Simple Interpreter
### Cut
  * Change backtracking, cut parts of the search tree
  * Prevents backtracking past the point where the cut is made
  * Still allows backtracking for search after the cut
  * The cut itself immediately succeeds as a subgoal
  * It **commits** Prolog to all the choice made
  * Example
  ```prolog
    q :- p.
    p :- a.
    p :- b, !, c.
    p.
    b :- m.
    m.
    b :- n.
    n.
  ```
  * q.fails since a fails, b succeeds but c fails.
  * The cut after b prevents using the fact after this rule,p.
  * If-then-else with Cut
    * Implement "if p then q else r" with cut
  ```prolog
  x :- p,!,q.
  x :- r.
  ```
  * If p succeeds: cut prevents r from being used
  * If p fails: normal backtracking, tries next rule with r
  * Version without cut
  ```prolog
  x :- p,q.
  x :- opposite-of-p,r.
  ```

### Negation
  * The meta-predicate "not"(\+ in Prolog) is defined by
  ```prolog
  not(X) :- X,!,fail.
  not(X).
  ```
  * If X then fail - so not(X) fails
  * Else(when x fails) not(X) succeeds
  * Prolog uses inference by failure to prove also called negation as failure(to prove)

### Prolog's Database
  * assert(Clause) : add in unspecified position, implementation dependent.
  * asserta(Clause) : add as first clause for the predicate at head of Clause
  * assertz: add as last Clause.
  * clause(Head,Body) : Find clause
  * retract(Clause) : erase the first clause in the current program that matches Clause
  * retractall(Head) : erase all clauses whose head matches Head

### Prolog Interpreter
  ```prolog
  interp(true) :- !.
  interp([P|Q]) :- !,interp(P),interp(Q).
  interp(P) :- clause((P :- Y)),interp(Y).
  interp(P) :- P.
  ```
