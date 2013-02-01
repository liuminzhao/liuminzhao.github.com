---
layout: post
title: "How to add CC license into LaTeX file and how to build LaTeX package"
description: ""
category: 
tags: [cc, latex]
---
{% include JB/setup %}

How to add CC license into LaTeX file and how to build LaTeX package
==========

# Introduction #

This article will introduce how to add CC into  file and how to build your own  package.

# What is CC #

CC is short for [Creative Commons](http://creativecommons.org/), which provides various kinds of licenses. Basically, **CC** license announces **some rights reserved** or **some perticular rights reserved** instead of **All rights reserved**. On their website, you could customize the license you want, just by clicking some buttons. Convenient html code will be produced.

# CC license in  slides #

However, those codes are only for html, in order to embed **CC** license into  slides, usually beamer slides, I found the following historical, ugly, but ready-eat  package **cclicenses** [CTAN](http://www.ctan.org/tex-archive/macros/latex/contrib/cclicenses/). Here is how it works:

put the following code in the preamble,

    \usepackage{cclicenses}                        

then follow the instruction in the help pdf for **cclicenses** package above.

Fortunately, I found this post by [Sebastian Pipping](http://blog.hartwork.org/?p=52). 

# ccbeamer #

One thing Sebastian Pipping mentioned is that it is not a **real**  package, thus to be a legitimate lazy man, I modified his package a little and built this **ccbeamer**  package.

# How to make your own  package #

Referring to this web page, I did as follows:

1. Rename Sebastian's `ccbeamer.tex` to `ccbeamer.sty` (used to put all your command into .sty file)

2. For your  distribution, (mine is TeXlive 2009) , find where  packages are installed. (mine is `usr/local/texlive/2009/texmf-dist/tex/latex`)

3. make directory, and put creative commons and ccbeamer.sty in.

4. use texhash to refresh your  database.

so if you download my modified ccbeamer  package, what you need to do is just to extract the zip file into where your  packages are installed, and refresh the database, put
    
    \usepackage{ccbeamer}                        

in your preamble.

For more options, read the **ccbeamer.sty** file.

