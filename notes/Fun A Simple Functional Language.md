---
title: 'Fun: A Simple Functional Language'
tags: [Notebooks/Cmput 325]
---

**[Fun: A Simple Functional Language](https://webdocs.cs.ualberta.ca/~mmueller/courses/325-Winter-2019/slides/Fun.pdf)**

## Atoms
  * a
  * id73
  * helloworld
  * -15
  * 3.1415
## Lists
  * (a (b) c (d))
  * (a b c d)
  * (((((((((()))))))))(((()))))
## Functions
  **first**
  ```lisp
   first( (a b c) ) -> a
   first( (((a) b) c) ) -> ((a) b)
   first( (((()))) ) -> ((()))
  ```
  **rest**
  ```lisp
  rest( (a b c) )-> (b c)
  rest( (a b) )-> (b)
  rest( (a) )-> ()
  ```
  **cons**
  ```lisp
  cons(a, () ) -> (a)
  cons(a, cons(cons(b, ()  ), ()  )  ) -> (a  (b) )
  ```
  **null**
  ```lisp
  null(x) true iff x is an empty list
  ```
  **eq**
  ```lisp
  eq(x,y) true iff x and y are the same atom
  ```
  **atom**
  ```lisp
  atom(x) true iff x is an atom
  ```
  **append**
  ```lisp
  append( (1 2), (a b c) )-> (1 2 a b c)
  append( ((1) 2), (a (b c)) )->
((1) 2 a (b c))
  ```
  **last**
  ```lisp
  last(L), returns the last element of a non-empty list
  last(L) = if null(r(L)) then f(L) else last(r(L))
  ```
  **removeLast**
  ```lisp
  removeLast(L), returns a copy of the list without the last element
  removeLast(L) = if null(r(L)) then () else cons(f(L), removeLast(r(L))
  ```
  **reverse**
  ```lisp
  reverse(L) = if null(L) then L, else append(reverse(r(L)), cons(f(L), ()))
  reverse(  (a b c)  ) --> (c  b  a)
  ```
## BinaryTree
  **EmptyTree**
  ```lisp
  nil
  ```
  **Non-empty tree**
  ```lisp
  (left-subtree node-value right-subtree)
  ```
