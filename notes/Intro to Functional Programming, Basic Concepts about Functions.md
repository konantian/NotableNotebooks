---
title: 'Intro to Functional Programming, Basic Concepts about Functions'
tags: [Notebooks/Cmput 325]
---

**[Intro to Functional Programming, Basic Concepts about Functions](https://webdocs.cs.ualberta.ca/~mmueller/courses/325-Winter-2019/slides/FPIntro.pdf)**

## Destructive Assignment
```java
int x =3;
x=5;
```
```java
int y;
y=4;
```
## Statements change program state directly
### Problems
* Parallel programming
* Side effects
* Anyone can write anywhere
### Solutions
1.Functional Programming
  * "write-one" and nver changed
  * withoutlosing efficiency, oftern better
  * Cleaner and esier to understand
  * Easier to use in new computing environments
  
2.Encapsulate access
  * Use only get/set
  * Use private fields
  
## Directly mapped to low-level operations
### Declarative Programming
1.Specify the logic of your problem
2.Let the program figure out the solution steps
3.No direct step by step control flow
4.Subparadigms
  * Constraint Programming
    * Specify constraints on the solution
    * Let a constraints solver find solutions
  * Logic Programming
    * Prolog
    * Database query language
  * Functional Programming
    * Pure functional programming
    * Lisp
