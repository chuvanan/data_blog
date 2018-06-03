---
title: Notes on installing R from source
author: An Chu
date: '2018-05-29'
slug: notes-on-installing-r-from-source
categories:
  - R
tags:
  - R
  - Ubuntu
---

Lately, I decided to install R version 3.5.0 from source because the Ubuntu's R
repository maintainers are way too late to get the binary up and running. I did
not complain about their decent voluntary works, I just can't wait to try out new
features and improvements. Also, I've read some good
[things](https://unix.stackexchange.com/questions/152346/what-is-the-difference-between-building-from-source-and-using-an-install-package)
about building software from source, so this is a chance to boost up my technical
expertise.

The installation process was actually not so hard as I thought. But it still
took me three times to get the configurations right on my computer systems. In
what follows, I note down some issues which I encountered during the process.

* R failed to recognize **tcltk** capability even though I have **tcl** and
  **tk** installed and up-to-date on my machine. I skipped this immediately
  because I hardly ever do GUI programming in R.

* R declined to activate cairo graphics engine despite that capability check
  returned `TRUE`. After three minutes searching around the Web, I found a quick
  hack as the following:

```r
## put these codes in .Rprofile
setHook(packageEvent("grDevices", "onLoad"),
        function(...) grDevices::X11.options(type = 'cairo'))
options(device = 'x11')
```

- Since I maintain multiple versions of R, I have to set up symbolic links
  pointing to R 3.5.0 executable files (`R`, `Rscript`) so that they are always
  searched by my system's **which R**.
