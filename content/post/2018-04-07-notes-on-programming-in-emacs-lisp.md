---
title: Notes on Programming in Emacs Lisp (1)
author: An Chu
date: '2018-04-07'
slug: notes-on-programming-in-emacs-lisp
categories: []
tags:
  - emacs
---

# 1. List processing

* Lisp != "Lots of Isolated Silly Parentheses"

* Lisp == "LISt Processing"

* List data structure: surrounded by parentheses, preceded by a single
  apostrophe, elements separated by space(s). List can be nested in another
  list. Examples:

Open elisp REPL in Emacs: `M-x ielm`.

```lisp
'(rose violet daisy buttercup)
'(rose (violet (daisy buttercup)))
```

* In Lisp, both data and programs are represented the same way:

```lisp
(+ 2 2)
4
(+ (- 4 1) 1)
4
```

* Lisp atoms: 'indivisible' parts (or elements inside parentheses). Examples:
  numbers (1, 2, 3); symbols (`forward-line`), string ("this is a text").

* The printed representation of both atoms and lists are called symbolic
  expressions or, more concisely, s-expressions.

* Evaluation: `'` means quote, do nothing except return the list itself. If no
  quote, list are evaluated by the first symbol, aka. function. In Emacs: `C-x
  C-e` == `eval-last-sexp`, or `C-j` (kind of elisp notebook)

* `C-M-x` for evaluating Lisp functions.

* Variable: a symbol that has a value attached to it.

Some built-in variables: `fill-column`

* `message` function: send messages to users, in echo area.

```lisp
(message "helo")
"helo"
(message "The name of this buffer %s" (buffer-name))
"The name of this buffer *scratch*"
```

* Setting value of a variable

```lisp
;; using set (noted: both variable and value must be quoted unless you want otherwise)
(set 'flowers '(rose violet daisy buttercup))
;; (rose violet daisy buttercup)
```

```lisp
;; using setq, automatically quoted the variables
(setq trees '(pine fir oak maple)
      herbivores '(gazelle antelope zebra))
(gazelle antelope zebra) ; last value is returned
```

# 2. Practicing Evaluation

This section for Emacs users.

```lisp
;; get buffer name
(buffer-name)
"elisp-prog.el"

;; name of file associated with the buffer
(buffer-file-name)
"/home/anchu/elisp-prog.el"

;; get the buffer itself
(current-buffer)
#<buffer elisp-prog.el>

;; the most recently selected buffer
(other-buffer)
#<buffer *Messages*>

;; jump the other buffer
(switch-to-buffer (other-buffer))

;; number of characters in the buffer
(buffer-size)
1109

;; current position of cursor
(point)
1124

(point-max)
1143

(point-min)
1
```
