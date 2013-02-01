---
layout: post
title: "Notes with org-slidy"
description: ""
category: 
tags: [org-mode, slidy]
---
{% include JB/setup %}

Notes: Make Slides with Org-mode and Slidy (org-slidy)
==========

# Reference #

- <http://tucker-kellogg.com/blog/2012/06/04/making-interactive-slides-with-org-mode-and-googlevis-in-r/>
- <http://www.r-bloggers.com/interactive-html-presentation-with-r-googlevis-knitr-pandoc-and-slidy/>
- <http://dl.dropbox.com/u/7586336/blogger/Cambridge_R_googleVis_with_knitr_and_RStudio_May_2012.html#(1)>
- <https://github.com/dov/org-slidy>
 
# Usage #

* Download [org-slidy](https://github.com/dov/org-slidy)
* put org-htmlslidy.el in Emacs load path
* `(require 'org-htmlslidy)` in .emacs file
* copy htmlslidy.org, slidy.js, slidy.css, jquery.js, org-slides.js in source directory
* `M-x load-library org-htmlslidy`
* put the following in org file : 
        
		#+TITLE:
        #+AUTHOR:
        #+BIND: org-export-html-preamble nil
        #+SETUPFILE: ~/Dropbox/_support/org/htmlslidy.org
        #+PROPERTY: results output html
        #+PROPERTY: exports results

* `C-c C-e b`

## Source block ##

`#+BEGIN_SRC R :results output html`
	    
		#+BEGIN_SRC R :cache yes
		library(>...)
		#+END_SRC

other options in R source code block:

	#+BEGIN_SRC R :results value raw :exports results :colnames yes

## Plot ##

	#+BEGIN_SRC R :results graphics raw :exports both :file easyplot.png

## HTML block ##

	#+HTML: <iframe align="right" width="420" height="315" src="http://www.youtube.com/embed/hVimVzgtD6w" frameborder="0" allowfullscreen></iframe>

## Example Block ##

	#+BEGIN_EXAMPLE 
	#+TITLE:
    #+SETUPFILE: htmlslidy.org
	#+BIND: org-export-html-preamble nil
    #+END_EXAMPLE
