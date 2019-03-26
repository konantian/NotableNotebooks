---
title: Prolog 2-Built in predicates
tags: [Notebooks/Cmput 325]
created: '2019-03-26T21:19:31.847Z'
modified: '2019-03-26T22:18:55.692Z'
---

# Prolog 2-Built in predicates
## Built-in operators
### Arthmetic
  ```prolog
  ?- X is 1 + 2*3.
  X = 7.
  ?- X is (1+2) * 3.
  X = 9.
  ?- X is 3/4.
  X = 0.75.
  ?- 4 is 1+3.
  true.
  ?- 1 + 3 is 1+3. 
  false
  ```
### comparisons
  * comparisons: >,<,>=,=<

### Equality operators
  * X ```=``` Y(tries to make X, Y equal by unification)
  * X ```is``` Expr(evaluates Expre, then tries to make result equal to X)
  * T1 ```==``` T2(are two terms currently identical without unification)
  * **The ```=``` "operator" in Prolog is actually a predicate (with infix notation) =/2 that succeeds when the two terms are unified. Thus X = 2 or 2 = X amount to the same thing, a goal to unify X with 2.**
  * **The ```==``` "operator" differs in that it succeeds only if the two terms are already identical without further unification. Thus X == 2 is true only if the variable X had previously been assigned the value 2.**


### Non-Equality Operators
  * T1 \== T2(are two terms not identital without unification)
  * E1 =:= E2(are E1 and E2 equal-valued arithmetic expressions)
  * E1 =\= E2(are E1 and E2 different-valued arithmetic expressions)
  * **```\=``` means the two terms cannot be unified, i.e. that unification fails. As with all applications of negation as failure, "not unified" does not (and cannot) result in any unification between terms.**
  * **```\==``` means the two terms are not identical. Here also no unification takes place even if this succeeds.**

### is
  ```prolog
  ?- N is 3+6.
  N = 9
  ?- N is X + 5.
  ERROR
  ?- X is 3, N is X+5.
  X=3,N=8.
  ```
### Equal and identical
  ```prolog
  ?- 4 + 5 =:= 8+1
  true
  ?- X == X
  true
  ?- X == x
  false
  ?- X == Y
  false
  ?- X = Y, X == Y.
  X = Y
  ?- X == Y, X = Y.
  false
  ?- X = 3,X==3.
  X = 3.
  ?- X = 3, Y = 3, X == Y.
  X = Y, Y = 3.
  ```
### Non Identical
  ```prolog
  ?- X \== Y
  true
  ?- X \== 3
  true
  ?- X = 3, X \==3
  false
  ?- X \== X.
  false
  ?- 2+4 \== 7.
  true.
  ```

### Non-Equal Expressions
  ```prolog
  ?- 4 =:= 1+3.
  true.
  ?- 1+3 =:= 2+2.
  true
  ?- X =:= 1+3.
  ERROR
  ?- 1+3 =\= 2+2.
  false
  ?- 1+3 =\= 2+3.
  true.
  ```

### Meta-Logical Predicates
  * var(X) : **test whether X is uninstantiated**
  * nonvar(X): **opposite of var**
  * atom(X): **check if X is instantiated to an atom**
  * integer(X): **check if X is an integer**
  * number(X): **check if X is a number**
  * atomic(X): **true if X is either an atom or a number**

## Finding all solutions
  * Basic syntax: 
  ```prolog
  findall(Variable,Goal,Solutions).
  ```
  * Examples:
  ```prolog
  ?- findall(X,member(X,[a,a,b],Result).
  Result=[a,a,b].
  ?- findall(take(X),course(X),Courses).
  Courses = [take(cmput325),take(cmput175)].
  ?- findall(X,append(X,Y,[a,b,c],Result).
  Result=[[],[a],[a,b],[a,b,c]].
  ```

## Data Structures in Prolog
  * List
  ```prolog
  ?- [A|L]=[a,b,c].
  A=a,
  L=[b,c].
  ?- [a,b,X,d|Rest] = [a,b,c,d,e]. 
  X = c, Rest = [e].
  ?- [[a,b],c|L] = [a,b,c]. 
  false.
  ?- [a,b,c|L] = [a,b,c].
  L = [].
  ?- [a|[]] = [a]. 
  true.
  ```
  * Append
  ```prolog
  append([], L, L).
  append([A| L1], L2, [A|L3]) :append(L1, L2, L3).

  ?- append([a1, a2], [b1], A). 
  A = [a1, a2, b1].

  ?- append([1,2,3], [4,5], [1,2,3,4,5]). 
  true.

  ?- append([1,2,3], X, [1,3,2|Rest]). 
  false  .

  ?- append([1,2,3], X, [1,2,3|Rest]). 
  X = Rest.
  ```
  * Member and not_member
  ```prolog
  member(X, [X|_]).
  member(X, [_|L]) :- member(X, L).

  not_member(_, []).
  not_member(X, [Y|L]) :- X \== Y, not_member(X, L).
  ```

  * Reverse
  ```prolog
  reverse([], []).
  reverse([A|Rest], Rev) :- reverse(Rest, RevRest), append(RevRest,[A],Rev).
  ```

  * If-Then-Else
  ```prolog
  p(Input, result1) :- test1.

  p(Input, result2) :- opposite-of-test1, test2.

  p(Input, result3) :- opposite-of-test1, opposite-of-test2, test3.

  p(Input, result4) :- opposite-of-test1, opposite-of-test2, opposite-of-test3.
  ```

