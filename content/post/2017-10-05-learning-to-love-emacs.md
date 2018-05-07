---
title: Learning to love Emacs
author: An Chu
date: '2017-10-05'
slug: learning-to-love-emacs
categories: []
tags:
  - emacs
---

> If you are a professional writer – i.e., if someone else is getting paid to
> worry about how your words are formatted and printed – Emacs outshines all
> other editing software in approximately the same way that the noonday sun does
> the stars. It is not just bigger and brighter; it simply makes everything else
> vanish.

> --- Neal Stephenson - In the beginning ... was the command line

I am not a professional writer, or intend to be one. However, I make a living by
writing codes, so the choice of code editor matters. After having used a dozen
of text editors and programming softwares (commonly known as IDEs), I finally
found the one I love most, `Emacs`.

`Emacs`, a text editor, which is created by Dr. Richard Stallman at MIT, is a
huge software project and has a long, storied history dated back to
mid-1970s.


Why do I place my faith in the 40-year-old computer program, you may
ask. Here's my thoughts.

The simple fact is that text editing programs like `Emacs` and `Vim` are no
longer in their heyday.  So it is unusual to choose the 40-year-old text editor
given that there are so many IDEs flying around nowadays with all the good
things ('batteries') included (visual debuggers, semantic analysis of source
code, etc). And I've read that `Emacs` is often chosen by old school hackers,
not someone from non-CS background like me.

Honestly, it was not a love at first sight. I ran across `Emacs` about five
years ago while I was trying to learn Python, and later switching to R at the
time. Well, the first impression was ... not impressive. It was rather
frustrating, actually. How on earth I need to press Ctrl-x Ctrl-c to quit the
program, and I even couldn't manage to select a block of text. Also I didn't
have much chance to use it in my first job (survey researcher). So I left it
quickly, it probably seemed that we are not made for each other.

I had a bit of luck that I switched job two years later and went to work as a
data analyst in a company where R is a 'mainstream' language. Never imagine that
I would have to write codes 8+ hours a day; it's kind of a challenging and also
exciting job for me (I had no prior background in computer science or
alike). However, `Emacs` was still not my choice at that time.  RStudio, an IDE
developed by a R-specialized startup, was gaining ground in the R users
community. Yes, it is a very powerful software (many claim that it is arguably
the best IDE for R[^2]) and widely used. I used to spend hours reading
tutorials, slides and books, playing with every tips and themes, memorizing
every keyboard shortcuts of RStudio. It really helps me get along with R very
well. But I felt something missing. Felt is the key word here. I didn't know
what it was, the feelings just sticked around.

Then came Hadley Wickham - R wizard and Chief Scientist of RStudio - put in his
recent book[^3]:

> The only real competitor [of RStudio] is ESS, emacs speaks statistics, which is
> a rewarding environment if you’re willing to put in the time to learn emacs and
> customize it to your needs.

Maybe I could give it a second chance, I thought. Maybe the missing piece is the
challenging aspect of learning and mastering your tools. The greatest strength
of RStudio is that I find it quite easy to learn and use it fluently. At the
same time, I quickly get bored. Moreover, my productivity is constrained by the
IDE's functionality.  With `Emacs`, that's not true, you are only limited by
your own capability (and your needs). This is a deal-breaker.

> The editor should be an extension of your hand; make sure your editor is
> configurable, extensible, and programmable.

> --- The Pragmatic Programmer

I started over immersing myself in the world of `Emacs`. At first, it was a
painful learning journey, both physically[^4] and mentally given that `Emacs` is
well known for its steep (or spiral[^5]) learning curve and I had become
accustomed to tons of die-hard habits and tricks in 'modern' windowing
interfaces.

One of the first thing I had to do to learn `Emacs` is relearn many conventional
concepts. For example, `Emacs` has two actions to describe earsing text:
deletion and killing. Deletion means earsing text and not saving it while
killing means what most people call 'cut'. It keeps a 'kill ring', a history of
kills, similar to most people call a 'clipboard'. If you 'paste' something from
clipboard, it is called 'yanking'. It uses the term 'frame' to mean the usual
'window', and it uses 'windows' to display 'buffers' and a 'buffer' is what got
when you open a file. However, not every buffer contains a file. Sounds weird,
right?

Another 'strange' thing is the combination of multiple key strokes to perform an
action (called key bindings) - from handling files, navigating around buffers to
searching and editing text. Almost anything is able to have keyboard map, and it
is the killing feature.  You'll be amazed by how fast you can accomplish so much
using only your keyboard. They're optimized for editing text, and once you
master them, you can edit text very efficiently in any language.

The best thing about Emacs might be Elisp (or Emacs Lisp), a dialect of Lisp
programming language. Except for its core which are written in C for
efficiency's sake, Emacs was built entirely upon Elisp. Every feature is
actually an Elisp function, and you can write your own functions (extensions) to
Emacs which means everything can be tailored to your needs. For example:

```lisp
(defun anchu/insert-named-comment (cmt)
  "Make comment header"
  (interactive "sEnter your comment: ")
  (let* ((user-cmt (concat "## " cmt " "))
         (len-user-cmt (length user-cmt))
         (len-hyphen (- 80 len-user-cmt)))
    (insert user-cmt (apply 'concat (make-list len-hyphen "-")))
    (newline)
    (newline)
    )
  )
(define-key ess-mode-map (kbd "C-c C-a d") 'anchu/insert-named-comment)
```

This simple bit of code adds to Emacs the ability very similar to `Insert
Section (Ctrl+Shift+R)` in RStudio which I used a lot when writing R script. Of
course that you ought to take time to learn Elisp, but I think it is very
worthy. Many people have written lots of great things about Emacs, so I will
stop here. Just in case you are hooked, just give it a try with
[org-mode](https://orgmode.org/) (an effective system for managing TODO lists,
planning projects,...) first, you'll be amazed.

Disclaimer: Though I am an `Emacs` fanboys, I do not consider myself as a
religious follower in the Church of `Emacs`.[^1]

**References**

* <https://www.johndcook.com/blog/2008/04/27/one-program-to-rule-them-all/>

* <http://irreal.org/blog/?p=5685>

* <https://www.slideshare.net/yukihiro_matz/how-emacs-changed-my-life>


[^1]: <https://stallman.org/saint.html>

[^2]: <https://www.quora.com/What-are-the-best-choices-for-an-R-IDE>

[^3]: <http://r-pkgs.had.co.nz/intro.html>

[^4]: <https://en.wikipedia.org/wiki/Emacs#Emacs_pinky>

[^5]: <http://stackoverflow.com/questions/10942008/what-does-emacs-learning-curve-actually-look-like>
