---
title: Symbolic Expressions
tags: [Notebooks/Cmput 325]
created: '2019-01-22T20:25:17.440Z'
modified: '2019-01-27T17:47:08.580Z'
---

**[Symbolic Expressions](https://webdocs.cs.ualberta.ca/~mmueller/courses/325-Winter-2019/slides/symbolic-expressions.pdf)**
 
 **Symbolic Expression**
   * Known as S-Expression,s-expr,sexpr
   * Universal data structure for Lisp
     * All atoms, dotted parts and lists are S-Expressions
   ```lis
   (a . b)
   (a . (b . c))
   (1 2 3 (4.5))
   ```
 **Dotted Pairs**
   * second argument of cons can be **any** s-expression
   * **dots and many other special characters can be part of names in Lisp**
   * Whitespace needed to separate atoms from dots
   ```lisp
   (car '(a.b)) ; a variable "a.b"
   (cdr '(a.b)) -> NIL
   (car '(a . b)) ; dotted pair
   (car '(a . b)) -> NIL
   ```
   * Dotted Pairs may equal to Lists
   ```lisp
   (car '(a))
   A
   (cdr '(a))
   NIL
   (car '(a . nil))
   A
   (cdr '(a . nil))
   NIL
   (equal '(a) '(a . nil))
   T
   ```
   * Examples
   ```lisp
   ((1 . (2 . 3)) . 4)
   ((1 . 2) . (3 . 4))
   (car '((1 . 2) . (3 . 4))) -> (1 . 2)
   (cdr '((1 . 2) . (3 . 4))) -> (3 . 4)
   (caar '((1 . 2) . (3 . 4))) -> 1
   (cdar '((1 . 2) . (3 . 4))) -> 2
   (cadr '((1 . 2) . (3 . 4))) -> 3
   (cddr '((1 . 2) . (3 . 4))) -> 4
   ```
   * Dotted Pair vs List
   ```lisp
   (a . nil) = (a)
   (cdr '(a . nil)) = nil
   (cdr '(a)) = nil
   ```
   * every list can be rewritten as dotted pairs by repeatedly using car,cdr
   ```lisp
   (1 2 3 4) = (1 . (2 3 4)) = (1 . (2 . (3 4)) = (1 . (2 . (3 . (4)))) = (1 . (2 . (3 . (4 . nil)))
   ```
   * All these s-expr idential to (a b c)
   ```lisp
   (a b c . nil)
   (a b . (c . nil))
   (a . (b . (c. nil)))
   (a b . (c))
   (a . (b c))
   ```
   * Lisp prints s-expr in their simples form
     * Least amount of dots
     * Eliminate both the dot and the matching open/closing parentheses
   ```lisp
   '(a . (b . (c . nil))) -> (A B C)
   '(a b . (c . nil)) -> (A B C)
   ```
   * Advantages of Dotted Pairs
     * Saves memory
     * Simplifies access
     * Compare list (a b) and (a . b)
       * List takes two memory cells
       * Dotted pair only takes one cell
       * Easier access to b
   ```lisp
   (cdr '(a . b))
   (cadr '(a b))
   ```
   * Lists are special cases of s-expr
   * Check by car and cdr
   * Check by convert to simplest form
   
  
**Examples**
```lisp
'(a . b) ;a dotted pair between a and b
'(a . (b . c)) ; a dotted pair between a and dotted pair (b . c)
'(1 2 3 (4 . 5)) ; a list contains number 1 2 3 and dotted pair (4 . 5)

(car (cons 'x 'y)) -> x
(cdr (cons 'x 'y)) -> y

(car '(a.b)) -> a.b ;an atom a.b, not dotted pair
(cdr '(a.b)) -> nil

(car '(a . b)) -> a
(cdr '(a . b)) -> b

(car '(a)) -> a
(cdr '(a)) -> nil
(car '(a . nil)) -> a
(cdr '(a . nil)) -> nil
(equal '(a) '(a . nil)) -> T ;both are equal because they have same result on "car" and "cdr"

(cons 1 2) -> (1 . 2) ; building sexpr with cons
(cons (cons 1 (cons 2 3)) 4) -> ((1 . (2 . 3)) . 4)
(cons (cons 1 2) (cons 3 4)) -> ((1 . 2) . (3 . 4))

(car '((1 . 2) . (3 . 4))) -> (1 . 2)
(cdr '((1 . 2) . (3 . 4))) -> (3 . 4)
(caar '((1 . 2) . (3 . 4))) -> 1 
(cdar '((1 . 2) . (3 . 4))) -> 2 ;execute car first, then cdr, order from last to first
(cadr '((1 . 2) . (3 . 4))) -> 3
(cddr '((1 . 2) . (3 . 4))) -> 4

(1 2 3 4) == (1 . (2 3 4) == (1 . (2 . (3 4))) == (1 . (2 . (3 . (4)))) == (1 . (2 . (3 . (4 . nil))))

(a b c) == (a b c . nil) == (a b . (c . nil)) == (a . (b . (c . nil))) == (a b . (c)) == (a . (b c))

(print '(a . (b . (c . nil))) -> (A B C) ; print s-exper in their simplest form and the output has two lines since the quote 
                                 (A B C) ; also print the result

```
