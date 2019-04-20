---
title: Quiz review
tags: [Notebooks/Cmput 325]
created: '2019-04-19T18:56:00.656Z'
modified: '2019-04-20T20:51:04.094Z'
pinned: true
---

# Quiz review
## Quiz 7
1. Prolog predicates return their results by assigning values to free variables in a query.
:white_check_mark: **In prolog, there is no return variabels, it just assign the value to the variable**
2. A Prolog query must contain at least one variable.
:x: **Facts does not require variable**
3. Which of the following expressions are valid Prolog, and do not lead to a runtime error?
  * a. X is 3+5*7 (This will work, since there is no unbound variable in 3+5*7)
  * b. X=3, Y is X+3, Z is X+Y.(This will work, since every variable is bound before evaluation)
  * c. X=3, Z = X+Y, Y=5.(This will work, since there is no evaluation on variables that unbound)
  * d. Y is X+3, X=3(This will not work, X is unbound when evaluate the expression "X+3").
  * e. X=3, X+Y is 10(This will work, since there is no variable in Expression(10)).

4. The expression [_,_] matches any list with exactly two elements.
:white_check_mark:

5. The expression [_|_] matches any list with both properties: a first element exists, and the rest of the list is not empty.
:x: **It is true that a first element must exist, but the rest can be the empty list. So for example, the unification [_|_] = [a] succeeds.**

6. A list in Prolog can be written either with comma-separated elements, or with a vertical bar between first and rest. But you cannot have both commas and vertical bar in the same list.
:x: **You can have both**

7. The query append(X,X,X).will find at least one solution.
:white_check_mark: **X = []**

8. Consider the query: findall(X, append(X, Y, [1,2,3,4]), L).Which of the statements below are true? Check all that apply.
**he query succeeds, X can be any prefix of [1,2,3,4]., In the result, L is a list of lists, one of the lists is [1,2,3]**
9. When answering a query with one predicate, Prolog will try to match the query with all heads of predicates with the same name.
:white_check_mark: **Prolog will try to match all the heads and see if there are at least one head match the query. Otherwise, just return false**
10. In logic programming, function symbols are used only for creating data structures, not for expressing computation.
:white_check_mark:
## Quiz 8
1. If a program has several facts and rules for which their head matches a query, then Prolog will always try all facts before it tries any rules.
:x: **Prolog will go from top to bottom through the list of facts and rules.**
2. A single Prolog clause can contain at most one anonymous variable.
:x: **For example [_|_] is a valid expression that contains two.**
3. The Prolog query
?- X == Y.
will fail since X and Y are different variables.
:white_check_mark:
4. The Prolog test \== is the logical opposite of ==. Whenever == succeeds, \== would fail, and vice versa.
:white_check_mark:
5. Which of the following expressions are valid Prolog, and do not lead to a runtime error?
  * a. X is 3+5*7 (This will work, since there is no unbound variable in 3+5*7)
  * b. X=3, Y is X+3, Z is X+Y.(This will work, since every variable is bound before evaluation)
  * c. X=3, Z = X+Y, Y=5.(This will work, since there is no evaluation on variables that unbound)
  * d. Y is X+3, X=3(This will not work, X is unbound when evaluate the expression "X+3").
  * e. X=3, X+Y is 10(This will work, since there is no variable in Expression(10)).
6. The Prolog query
?- X = 3, Y = 3, X == Y.
will fail since X and Y are different variables, even though they have the same value.
:x: **this will success since X and Y have the same value**
7. The query
?- X = 7, atom(X).
will fail since X is an integer.
:white_check_mark:
8. The query
?- X = 7, nonvar(X).
will fail since X is a variable.
:x: **This iwll success, since X is an variable**
9. The query
?- findall(X, append(X,X,X), L).
will return with L bound to the list of all solutions for append(X,X,X).
:x: **It will not return, it will get into an infinite loop.**
10. With function not_member defined as in the slides, the query
?- findall(X,not_member(X,[1,2,4]),L).
will go into an infinite loop and never return.
:x: **It will return with something like L = [_6142].**

## Quiz 9
1. The following two terms unify X = f(Y,3).
:white_check_mark: **t1 = f(Y,3) t2 = f(Y,3) t1 = t2**
2. The following two terms unify f(3,X) = f(g(Y),5).
:x: **t1 = f(3,5),t2 = f(g(Y),5) t1 != t2**
3. The following two terms unify X=Y.
:white_check_mark: **t1 = X,t2 = X, t1 = t2**
4. The following two terms unify f(X,Y) = Z.
:white_check_mark: **t1 = f(X,Y) t2 = f(X,Y) t1 = t2**
5. The following two terms unify f(X) = f(1,2).
:x: **The number of arguments has to match**
6. The following two terms unify f(X, 1, Y) = f(g(Z), X, Y).
:x: **No, cannot solve. From X=g(Z) and X=1, we get g(Z) = 1 which does not match.**
7. Sometimes, Prolog will go into an infinite loop, even though a short proof of a query exists.
:white_check_mark:
8. Given the following Prolog program:

  wet :- rain.
  wet :- sprinkler.
  fertilized :- compost.
  fertilized :- fertilizer.
  sprinkler.
  rain.
  fertilizer.
  compost.
  grassgrows :- wet, fertilized.
  What is the first derived goal for the goal

  ?- grassgrows.
  **wet,fertilized**
9. Same program as question 8, same query: What is the second derived goal for the goal

  ?- grassgrows.
  **rain,fertilized**
10. Same program, same query: What is the third derived goal for the goal

  ?- grassgrows.
  **fertilized**




