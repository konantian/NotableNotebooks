---
title: Prolog 1-Introduction to Prolog
tags: [Notebooks/Cmput 325]
created: '2019-03-26T19:19:46.519Z'
modified: '2019-03-26T21:05:19.190Z'
---

# Prolog 1-Introduction to Prolog
## Prolog
  * A Prolog program consistes of clauses
  ```prolog
  Fact:len([],0).
      father(ken,mary).
  Rule:len([First|Rest]...).
       parent(X,Y) :- father(X,Y).
  ```
  * List in Prolog
  ```prolog
  [First|Rest].
  [a,b,c,d].
  [a,b,c|Rest].
  [[a,b],[[[],c],d,[]].
  ```
  * Variables in Prolog
    * Variables in uppercase
    * Constants are lowercase
  ```prolog
  variables:X,Y,First.
  constants:a,b,c,d.
  ```
  * The scope of a variable is limited to one clause or one query
  * Prolog: Specify what properties a solution should have, then let Prolog search for it

  ## Logic programming
    * Declarative style of programming
    * Write a specification of a solution to a problem
    * The specification is **executable** - Prolog can use it to find a solution
    * The core of Prolog is a **search process** to find such a solution

## Introduction to Prolog
  * Terms
    * A constant is a term
    * A variable is a term
    * Functions are terms
    * Terms can only be used as argument in predicates
  * **Functions**
    * Programs are collections of clauses with predicates
    * Computation is doing inference with predicates 
    * Data structure: terms, including terms with function symbols, lists 
    * In Prolog, the role of function symbols is very different 
    * Function symbols are used to structure data, not for computation 
    * There is no function application
  * Facts
    * A fact is also called un conditional clause.
    * Facts and rules can also contain variables. Those are always **universally quantified**.
  * Rules
    * Rules are conditional clauses
    * Head is true under the condition that the body is true.
    * The body can consist of a list of **atoms**, with commas in between. All of them must be true to imply that the head is true
  

  
