---
title: 'Built-in Lisp functions, binary tree'
tags: [Notebooks/Cmput 325]
---

**[Built-in Lisp functions, binary tree](https://webdocs.cs.ualberta.ca/~mmueller/courses/325-Winter-2019/slides/Lisp-builtin.pdf)**

## Functions
**if-then-else**
```lisp
(if (atom nil) 3 5) -> 3
(if (> 3 5) "3 wins" "5 wins") -> "5 wins"
```

**Variable number of argument**
```lisp
(+ 1 2 3 4 5) -> 15
(* 5 6 7 8 9) -> 15120
(append '(this) '(is) '(append) '(with) '(six) '(listed)) -> (this is append with six lists
```

**Logic Connectives and Test Predicates**
```lisp
(and E1 ... En)
(or E1 .. En)
(not E)
(numberp x);true if x is a number(integer or real)
(atom x);(true if x is an atom
(null x);true if x is an empty list
```

**Let**
  * Gives you "bound local variables"
  * Efficient
  * Avoid duplication
  
```lisp
(let ((x 3) (y 4)) (* (+ x y) x)) - > 21;replaces names x,y with their value 3,4
(let ((result (f x)) (* result result))
(defun f(x) (* 5 x))
(let ((y (f 3)))
  (cons y(cons (+ y 1)(cons (+ y 2) nil)))
```

**Let\***
  * For use one variable to define another
```lisp
(let* ((x 1) (y (+ x 1))) y)
```

**eq VS equal**
  * eq only true if both are equal atoms
  * eq runs in a single machine instruction
```lisp
(eq '(a b) '(a b)) -> NIL
```

**equal**
```lis
(defun equal (S1 S2)
    (if (atom S1) (eq S1 S2)
      (if (atom S2) nil
          (and (equal (first S1) (first S2))
      (equal (rest S1) (rest S2))) ) ) 
)
```

**cond**
  * The lisp function **cond** is one of the most useful
  * It is kind of case (or switch) statement
  * It can be used in place of nested if-then-else
```lisp
(cond (P1 S1);if p1 is true then S1
      (P2 S2);otherwise if p2 is true then s2
      ...
      (T Sn);last case:catch-all test T = true
 )
```

**List vs quote vs cons**
  * Use quote when everything is constant
  * Use list when some contents are the result of evaluating functions
  * Use cons for the result in recursion when you have computed a first element and the rest of a list
  * Use cons for dotted pairs

**car and cdr**
```lisp
 (car nil) =>  NIL  
 (cdr '(1 . 2)) =>  2
 (cdr '(1 2)) =>  (2)
 (cadr '(1 2)) =>  2 
 (car '(a b c)) =>  A
 (cdr '(a b c)) =>  (B C)
```

**combining multiple car and cdr**
```lisp
(caar x)   ==  (car (car x))
(cadr x)   ==  (car (cdr x)) 
(cdar x)   ==  (cdr (car x))
(cddr x)   ==  (cdr (cdr x)) 
(car x)    ==  (first x)
(cadr x)   ==  (second x) ==  (car (cdr x))
(caddr x)  ==  (third x)  ==  (car (cdr (cdr x)))
(cadddr x) ==  (fourth x) ==  (car (cdr (cdr (cdr x))))
```

**print**
```lisp
(print "Helloworld")
```

**format**
```lisp
(format t "The Result is S" (sin 3))
```
**random**
```lisp
(random N);generate random integer from 0 - N-1
(random F);random floating point number in range [0..F)
```

## Binary Tree
```lisp
(defun is_empty (Tr)
    (null Tr)
)
(defun create_empty ()
    nil
)
(defun create (L N R)
    (cons L (cons N (cons R nil)))
)
(defun node_value (Tr)
    (car (cdr Tr))
)
(defun left_subtree (Tr)
      (car Tr)
)
(defun right_subtree (Tr)
    (car (cdr (cdr Tr)))
)
(defun insert (Tr Int)
    (cond ((null Tr)
        (create (create_empty)
            Int
            (create_empty)))
    ((eq (node_value Tr) Int)
      Tr)
    ((< (node_value Tr) Int)
      (create (left_subtree Tr)
          (node_value Tr)
          (insert (right_subtree Tr) Int)))
    (T
      (create (insert (left_subtree Tr) Int)
          (node_value Tr)
          (right_subtree Tr)))
) )
```

## Accumulating parameters
  * Often used in functional programming
  * Helper function with an extra parameter
  * Extra parameter accumulates the required result

## Simple Recursion
  * No real computation until hits the base case,e.g.empty list

## Accumulator vs Standard Recursion
  * Standard recursion on a list
    * Recurse to the end on a list
    * Compute results on return from recursion
    * computes results bottom-up(right-to-left on a list)
  * Accumulator
    * computes or accumulates results-so-far
    * Computes results top-down(left-to-right on a list)
    * Needs an extra accumulator variable for partial result
  * Accumulator is not fit for traverse tree
    
##
