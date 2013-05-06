---
layout: post
title: "markdown notes"
description: ""
category: 
tags: [markdown]
---
{% include JB/setup %}

# Markdown Notes #

- help

	    C-c C-h
  
- header 
	  
	    C-c C-t

## Anchors : C-c C-a ##

- link: 

	    C-c C-a l 	
	
- wiki link:

	    C-c C-a w
	
## Commands: C-c C-c  ##

- run markdown

	    C-c C-c m
	
- preview

     	C-c C-c p
	
- save, current, preview

	    C-c C-c e
	
- view 

	    C-c C-c v
	
## iamge: C-c C-i ##

- image

	    C-c C-i i
	
## Physical styles: C-c C-p ##

- bold

	    C-c C-p b
	
- fixed width 

	    C-c C-p f
	
- italic
	
	    C-c C-p i
	
## logical styles: C-c C-s ##

- quote

	    C-c C-s b
	
- Code:
	
	    C-c C-s c
	
- emphasis 

	    C-c C-s e
	
- strong
	  
	    C-c C-s s
	
## Header: C-c C-t n ##

- title: 

	    C-c C-t t
	
- section 

	    C-c C-t s
	
## other: ##

- horizontal rule: 

	    C-c -
	
## Navigation ##	

	C-M-n , C-M-p

## second level ##

indent by four spaces 

------------------------

# [Pandoc User's Guide](http://johnmacfarlane.net/pandoc/README.html) #

    pandoc -o output.html input.txt
	pandoc -f markdown -t latex hello.txt 

* -f = from
* -t = to 
* -o = output

## PDF ##

	pandoc test.txt -o test.pdf 

* markdown2pdf

## writer options ##

* -s : appropriate header and footer
* --template=FILE : 
* --toc 

## Math ##

* -m
* --mathml
* --mathjax

## Templates ##

## Pandoc Markdown ##

## Header ##

2 kinds

* ===
* ## 

## Verbatim ##

four spaces indented 

## Code ##

* ~~~~~~~~~ or `
* no indent needed 

        ~~~~{r}
		x <- 3 
		~~~~~~~~~~~~

## List ##

four spaces rule 

* cut off list : insert comment 

## Tables  ##

pandoc extension

	-------------------------------
	first     set   fsdf     fsdafd
	------   ----   ------   ------
	afsdf    sff    fsfs       ffff
	-------------------------------

	: test

### Grid Tables works ###

: sample grid table 

	+---------------+---------------+--------------------+
	| Fruit         | Price         | Advantages         |
	+===============+===============+====================+
	| Bananas       | $1.34         | - built-in wrapper |
	|               |               | - bright color     |
	+---------------+---------------+--------------------+
	| Oranges       | $2.10         | - cures scurvy     |
	|               |               | - tasty            |
	+---------------+---------------+--------------------+

and can use [Emacs table mode](http://table.sourceforge.net/)

or use **orgtbl-mode** 


## Title block ##

pandoc extension 

    % title
	% author(s) (separated by semicolons)
	% date 

## Superscripts and subscripts ##

pandoc extension

     ~2~ and 2^10^

## Math ##

pandoc extension

use double dollar sign 

    $$\alpha$$

# Slides with Pandoc #

    -i : make slides show incremental 
     pandoc -s --mathml -i -t dzslides input.md -o output.html

## Image size , center ##

Hello there!

![center](/images/hello.jpg)

use absolute directory:

	![Bilby Stampede](https://github.com/images/logo.png)

embed html in markdown

	<div style="float:right"><img src="testtaking.jpg" style="float:right;margin:0 10px 10px 0" width="80%"></div>

###### This is an image

	```
	Hi!
	
	[alt=center] {
	display: block;
	margin: auto;
	}

	h6 {
	font-weight: normal;
	text-align: center;
	}
	```

## Verbatim ##

`code `

or just begin with four spaces
