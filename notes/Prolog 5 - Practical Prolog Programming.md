---
title: Prolog 5 - Practical Prolog Programming
tags: [Notebooks/Cmput 325]
created: '2019-03-27T22:23:50.801Z'
modified: '2019-03-28T01:03:43.290Z'
---

# Prolog 5 - Practical Prolog Programming
### Order in Prolog
  * From pure logic point of view, order of clauses of subgoal should not matter
  * In practice, it often matters a lot
  * Order of subgoals can also be important

### Transitive Relation
  A relation R is **transitive** if 
  whenever R(X,Y) and R(Y,Z) hold, then R(X,Z) is also true
  ```prolog
  tran(X,Y) :- p(X,Y).
  tran(X,Z) :- p(X,Y), tran(Y,Z).
  ```

### Disjunction in Prolog
  ```prolog
  banana(X) :- yellow(X).
  banana(X) :- green(X).
  or
  banana(X) :- yellow(X) ; green(X).
  ```
