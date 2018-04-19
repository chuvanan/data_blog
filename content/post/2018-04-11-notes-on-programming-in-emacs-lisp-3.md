---
title: Notes on Programming in Emacs Lisp (3)
author: An Chu
date: '2018-04-11'
slug: notes-on-programming-in-emacs-lisp-3
categories: []
tags:
  - emacs
---

# More on function

* Short form:

```lisp
(defun <function_nam> (<parameters>) (<body>))
```

```lisp
(defun my-sum (a b c) (+ a b c))
my-sum

(my-sum 1 2 3)
6
```

* Anonymous function, a.k.a lambda functions:

```lisp
(lambda (x) (+ x 3))
(lambda
  (x)
  (+ x 3))
```

To call lambda function, there are two methods: i) use list method or ii) call
`funcall`:

```lisp
((lambda (x) (+ x 3)) 4)
7

(funcall (lambda (x) (+ x 3)) 4)
7
```

Lambda function can be stored in a variable:

```lisp
(defvar add3 (lambda (x) (+ x 3)))

(funcall add3 10)
13

(mapcar add3 '(1 2 3 4 5))
(4 5 6 7 8)
```

Very similar to anonymous function in R:

```r
> (function(x) x + 3)(4)
[1] 7

> add3 <- (function(x) x +3)
> add3
function(x) x +3

> add3(10)
[1] 13

> Map(add3, 1:5)
[[1]]
[1] 4

[[2]]
[1] 5

[[3]]
[1] 6

[[4]]
[1] 7

[[5]]
[1] 8
```
