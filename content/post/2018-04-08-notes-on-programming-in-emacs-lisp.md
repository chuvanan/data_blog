---
title: Notes on Programming in Emacs Lisp (2)
author: An Chu
date: '2018-04-08'
slug: notes-on-programming-in-emacs-lisp
categories: []
tags:
  - emacs
---


# 3. Function

* Primitive functions written in C. Main reason: portability

* Function anatomy:

  * function name
  * arguments
  * documentaion (optional)
  * an expression to make the function interactive (optional)
  * function body

```lisp
(defun multiply-by-seven (number)
  "Multiply NUMBER by seven."
  (* 7 number))

(multiply-by-seven 3)
21

;; make function interactive
(defun multiply-by-seven (number)
  "Multiply NUMBER by seven."
  (interactive "p") ; p - pass the prefix argument to the function
  (message "The result is %d" (* 7 number)))
```

* Emacs has a dozen of interactive codes (see
  [more](https://www.gnu.org/software/emacs/manual/html_mono/elisp.html#Interactive-Codes))

* Install function for temprary use, `C-x C-e`. To use code permanently, put
  function in `.emacs` initialization file.

* Special form: `let` which is used to bind a symbol to a value, or to create a
  local variable (visible only in `let` expression). In Emacs Lisp, scoping is
  dynamic, not lexical.

* `let` structure:

```lisp
(let ((variable value)
      (variable value)
      ...)
  body...)
```

```lisp
(let ((zebra "stripes")
      (tiger "fierce"))
  (message "One kind of animal has %s and another is %s."
           zebra tiger))
```

* Uninitialized variables return `nil`

```lisp
(let ((birch 3)
      pine
      fir
      (oak 'some))
  (message
   "Here are %d variables with %s, %s, and %s value."
   birch pine fir oak))
"Here are 3 variables with nil, nil, and some value."
```

* `if` statement

```lisp
(setq my-name "anchu")
(if (equal my-name "anchu")
    (message "My name is %s" my-name))
"My name is anchu"
```

* `if-then-else` expression

```lisp
(defun type-of-animal (characteristic)  ; Second version.
  "Print message in echo area depending on CHARACTERISTIC.
     If the CHARACTERISTIC is the string \"fierce\",
     then warn of a tiger; else say it is not fierce."
  (if (equal characteristic "fierce")
      (message "It is a tiger!")
    (message "It is not fierce!")))

(type-of-animal "fierce")
"It is a tiger!"

(type-of-animal "striped")
"It is not fierce!"
```
* `nil` means empty list and false

* Special form: `save-excursion`. It saves the location of point, executes the
  body of the function and then restores points to previous position. Template:

```lisp
(save-excursion
  first-expression-in-body
  second-expression-in-body
  third-expression-in-body
  ...
  last-expression-in-body)
```

# 4. Basic operation

```lisp
;; Arithmetic
(+ 20 30)
50

(- 100 80)
20

(+ 1 2 3 4 5)
15

(* 1 2 3 4 5)
120

(/ 100 20)
5

(> 10 1)
t

(< 2 8)
t

(< 8 2)
nil

(= 2 4)
nil

(equal 2 2)
t

(exp -1)
0.36787944117144233

(log 10)
2.302585092994046

(sin pi)
1.2246467991473532e-16

(tan 90)
-1.995200412208242
```

```lisp
;; Comparision
(equal (list 1 2 3 4) (list 1 2 3 4))
t

(eq 'x 'x)
t

(string= "a" "a")
t

(string= "a" "A")
nil

(string-equal "z" "z")
t

(string< "a" "b")
t

(string-lessp "a" "b")
t

(equal '(1 2) (list 1 2))
t

(eq '(1 2) (list 1 2))
nil
```

* Type predicates

    * null: test if argument is nill
    * numberp
    * stringp
    * symbolp
    * atom: test if argument is not a list or pair
    * listp
    * consp: test if it is a pair
    * vectorp: test if it is a vector
    * bufferp: is arg a buffer object
    * windowp: is arg a window object
    * framep: is arg a frame object
    * processp: is arg a process

* Get object type with `type-of`

```lisp
(type-of 1)
integer

(type-of "12")
string

(type-of '(1 2 3))
cons

(type-of '(a . "e"))
cons

(type-of (current-buffer))
buffer

(type-of 'current-buffer)
symbol
```
