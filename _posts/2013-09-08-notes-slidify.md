---
layout: post
title: "notes slidify"
description: ""
category:
tags: [slidify]
Time-stamp: "liuminzhao 03/15/2014 18:47:23"
---
{% include JB/setup %}

1. <http://ramnathv.github.io/slidifyExamples/>
2. <https://github.com/ramnathv/slidifyExamples/tree/gh-pages/examples>
3. <https://io-2012-slides.googlecode.com/git/template.html?presentme=true>

# General #

	library(slidify)
	author("project")
	slidify("index.Rmd")
	publish(user = "User", repo = "repo")

	logo: aa.png
	biglogo: aa.png
	license: by-nc-sa
	widgets: [mathjax, bootstrap]
	github: {user: name, repo: reponame}
	hitheme: tomorrow
	assets: {js: 'test.js'}

png put under `assets/img/aa.png`

use `---` to separate frames

	publish('dir', host = 'dropbox')
	publish(user = '', repo = '', host = 'github')

for `github`, the repo should be `gh-pages`.

# IO2012 #

## list ##

### Nested ###

	>- Thing 1
		- Point 1
	>- Thing 2
		- Point 2

### Animated ###

	> 1. xx
	> 2. yy

### Unordered ###

	> - xx
	> - yy

## Tables ##

	Column X | Column Y
	---------|---------
	Row 1    |  Row 1
	Row 2    |  Row 2

Make table in  org-mode then copy to Rmd file:

	(defun markdown-regexp-right (beg end)
	(interactive "r")
	(replace-regexp "-\|[^-]" "-:|\n" nil beg end)
	(replace-regexp "-\\+-" "-|-" nil beg end)
	)

	|twocolumn||
	|1st | 2nd |

## Background ##

	--- bg:#662c91
	--- bg:#EEE

## Mathjax ##

	$$
	\begin{align}
	blabla
	\end{align}
	$$
	<br />

## Layout ##

Two column

	--- &twocol
	*** left
	xxx
	*** right
	yyy

## Bootstrap ##

### Blocks ###

	<div class="alert alert-info">
	<p>This is an alert info block which should render in blue</p>
	</div>


# landside #

	framework: landslide
	landslide: theme: clean

	---
	<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js"></script>

# dzslides #

	framework: dzslides

## footer ##

	<footer> by *** </footer>

# shower #

	framework: shower

## Figures ##

	--- .cover #FitToHeight
	--- .cover .w #FitToWidth

	<img style="float:middle" src="assets/img/polya.jpg" />
	<img align="middle" src="assets/img/polya.jpg" />

### center

<http://stackoverflow.com/questions/16904054/slidify-how-to-position-an-image>

manually:

	<div style='text-align: center;'>
    <img height='560' src='x.png' />
	</div>

auto:

	<!-- Limit image width and height -->
	<style type='text/css'>
	img {
    max-height: 560px;
    max-width: 964px;
	}
	</style>

	<!-- Center image on slide -->
	<script src="http://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.7.min.js"></script>
	<script type='text/javascript'>
	$(function() {
    $("p:has(img)").addClass('centered');
	});
	</script>

put them right below the description

## shout ##

	--- .shout #warning

## blockquote ##

	--- #blockquote
	> **

# Deck.js #

	framework: deckjs
	deckjs:
		theme: web-2.0
	highlighter: highlight.js

# Citation #

	library(knitcitations)
	bib <- read.bibtex('reference.bib')
	`r citet(bib[['yu2001']])` for inline

Print all :

	```{r results = "asis", echo = FALSE}
	bibliography()
	```

# Customize #

change `assets/css` file and `assets/layouts/slide.html`, can also
customize own class, id, and key (like `.definition` and `.example`)

For example, create `mytwocol.html` under `assets/layouts/slide.html`:

	<slide class="{{ class }}" id="{{ id }}">
	<hgroup>
		{{{ header }}}
		</hgroup>
	<article>
    <hr noshade size=4 color='red'>
    {{{ content }}}
    <div class='left' style='float:left;width:{{{ w1 }}}'>
     {{{ left }}}
    </div>
    <div class='right' style='float:right;width:{{{ w2 }}}'>
     {{{ right }}}
    </div>
	</article>
	</slide>
