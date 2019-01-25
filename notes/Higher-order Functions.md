---
title: Higher-order Functions
tags: [Notebooks/Cmput 325]
---

**[Higher-order Functions](https://webdocs.cs.ualberta.ca/~mmueller/courses/325-Winter-2019/slides/higher-order.pdf)**

**Higher-order Functions**
  * Definition
    * Takes other functions(s) as input
    * Produces functions(s) as output
  * Often used to separate:
    * A computation pattern
    * A specific action
    
 
**Map**
  * Apply a given function to each element in a list
  * Collect all the results in a list
  * Idea: write a function map that
    * Can take **any** function f as an argument
    * Applies f to every element in a given list
    * Returns the list of results
    * Input: List(e1 e2 ... en)
    * Output: List (f(e1) f(e2) ... f(en))
```lisp
(defun plus1(x) (+ x 1)) -> plus1
(mapcar 'plus1 '(1 2 3 4 5)) -> (2 3 4 5 6)
(defun inc(N) (cons (car N) (+ 100 (cdr N)))) -> INC
(mapcar 'inc' ((John . 23000) (Mary . 54560)) -> ((JOHN . 23100) (MARY . 54600))
```

**Reduce**
  * Idea:
    * In a list, repeatedly apply the same function to two arguments, which produces a single argument
    * Given a function g, its identity id, and a list L = (A1 A2 ... An)
    * Compute (g A1 (g A2 ... (g An id) ...))
```lisp
(reduce '* '(2 6 4)) -> 48
(reduce 'append '((a b) (c) (d e))) -> (A B C D E)
(reduce '+ (mapcar 'cdr (mapcar 'inc L)))
```

**MapReduce for Big Data**
  * Scenario: huge amounts of data spread over many disks(distributed memory)
  * Given a statistical query on all that data
    * find all overdrawn accounts
    * find all webpages containing the word "Lisp"
    * find all images of cats
  * Map: apply the same operation to each data item
  * Reduce: compute summary statistics, or sort and present the top 10 pages
  
  
**MapReduce in the Real World**
  * Provides an easy API for using large clusters
  * The aim is to hide the complexity of the distributed computing support
  * Performance can be worse than specialized database technology
  * Good for quick, "one shot" tasks
  
**Filter**
  * Goal: Select all elements from a list which satisfy a given test predicate Pred
 
**Vector**
  * Apply a list F of functions to an object x and get the list of all results of the applications

**apply and funcall**
  * Using **apply** and **funcall** tells Lisp that there is a function to be called
  * These two built-in functions have the same functionality but differ in syntax
  * apply expects a list with all arguments
  ```lisp
  (defun mymapcar1 (f L)
    (if (null L)
      nil
      (cons (funcall f (car L))
            (mymapcar1 f (cdr L)))
       )
   )
   ```
