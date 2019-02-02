---
title: Lambda Calculus
tags: [Notebooks/Cmput 325]
created: '2019-02-01T22:48:43.464Z'
modified: '2019-02-01T23:41:11.901Z'
---

# Lambda Calculus

### Lambda functions
 * `Are function definitions without names`
 * Good for
   * A function was the result of a higher-order function
   * We tried to return this newly computed function
  * Lambda definition
  ```lisp
  (lambda (x1 . . . xn) body)
  ```
  * Important: A lambda function is a definition, not an application
  * Lambda application
  ```lisp
  ((lambda (x1 . . . xn) body) a1 ... an)
  ```
  * Example
  ```lisp
  ((lambda (x y) (+ x y)) 2 3) -> 5
  ((lambda (x y) (+ (* x x) y)) 4 6) -> 22
  (mapcar (lambda (x) (+ x 1)) '(1 2 3 4 5)) -> (2 3 4 5 6)
  ```
  * **Important:** never quote the function but list
  * Quoting a lambda expression works with Lisp-1 but not sbcl
  * Use function and funcall to help Lisp understand lambda functions/applications
  ```lisp
  (mapcar (function (lambda (x) (+ x 1))) '(1 2 3 4 5)) -> (2 3 4 5 6)
  ```
  * Function vs funcall and apply
    * function for "function definition"
    * funcall and apply for"function application"
  ```lisp
  (lambda (x) (+ x 1)) 100)
  (funcall (function (lambda (x) (+ x 1))) 100) -> 101
  (funcall (lambda (x) (+ x 1)) 100) -> 101
  (funcall (function (lambda (x y) (+ (* x x ) y))) 4 6) -> 22
  (apply (function (lambda (x) (+ x 1))) '(3)) -> 4
  ```
  
## Lambda Calculus
  *
