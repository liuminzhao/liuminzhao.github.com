---
layout: post
title: "notes slidify"
description: ""
category:
tags: [slidify]
Time-stamp: "liuminzhao 09/09/2013 15:23:48"
---
{% include JB/setup %}

1. <http://ramnathv.github.io/slidifyExamples/>
2. <https://github.com/ramnathv/slidifyExamples/tree/gh-pages/examples>

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
