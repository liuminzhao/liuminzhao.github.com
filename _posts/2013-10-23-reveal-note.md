---
layout: post
title: "reveal note"
description: ""
category:
tags: [org-mode, emacs, html5]
Time-stamp: "liuminzhao 03/03/2014 22:47:19"
---
{% include JB/setup %}

Making html5 slides (reveal.js) with org-mode
====

Reference:

1. <https://github.com/yjwen/org-reveal/blob/master/Readme.org>
2. <http://blog.jr0cket.co.uk/2013/10/create-cool-slides--Org-mode-Revealjs.html>

# Invoke #

In `.emacs`:

	(setq org-reveal-root "file:///Users/liuminzhao/dev/reveal.js")

or in org file:

	#+REVEAL_ROOT: file:///Users/liuminzhao/dev/reveal.js

shortcut:

	C-c C-e R R

# Setup #

	#+Title:
	#+Author:
	#+Email:

	#+OPTIONS: toc:nil reveal_mathjax:t
	#+REVEAL_TRANS: linear {default, cube, page, concave, zoom, linear, fade, none}
	#+REVEAL_THEME: night {default, beige, sky, night, serif, simple, moon}
	#+REVEAL_ROOT: file:///Users/liuminzhao/dev/reveal.js

# Structure #

- First level: `*`
- Second level: `**`

A new slide begins after `#+REVEAL` keyword

	#+REVEAL: split

# frag #

fragment

	#+ATTR_REVEAL: :frag highlight-blue {roll-in, grow, shrink, fade-out,
	highlight-red, highlight-blue}

must follow directly

# Data State #

under slides, change slide property.

   :PROPERTIES:
   :reveal_data_state: alert {alert, blackout, soothe}
   :END:

# Plug-ins #

   - reveal-control : Show/hide browsing control pad.
   - reveal-progress : Show/hide progress bar.
   - reveal-history : Enable/disable slide history track.
   - reveal-center : Enable/disable slide centering.

   - `#+OPTIONS` tags:\\
		reveal_control, reveal_progress reveal_history
		reveal_center, reveal_rolling_links, reveal_keyboard reveal_overview

# Math

	${n! \over k!(n-k)!} = {n \choose k}$

	#+OPTIONS: toc:nil reveal_mathjax:t

# Toc #

	#+OPTIONS: toc:t

# Speaker Notes #

Press `s`

Also use

	#+BEGIN_NOTES
	Enter speaker notes here.
	#+END_NOTES

# Disable Heading Numbers

	#+OPTIONS: num:nil

# Internal links

Use custom id property

# Pandoc  #

Converting from markdown file

	pandoc -s -S index.md -o index.org --from markdown-yaml_metadata_block

# Theme:

## single color background:

	:PROPERTIES:
	:reveal_background: #123456
	:END:

## single image background

	:PROPERTIES:
    :reveal_background: ./images/whale.jpg
    :reveal_background_trans: slide
    :END:

# Example #

	#+Title: Presenting with Emacs
	#+Author: Minzhao Liu
	#+Email: liuminzhao@gmail.com

	#+OPTIONS: toc:t reveal_mathjax:t num:nil
	#+REVEAL_TRANS: zoom
	#+REVEAL_THEME: serif
	#+REVEAL_ROOT: file:///Users/liuminzhao/dev/reveal.js
	#+STARTUP: latexpreview

	* Heading 1

	$$\lambda$$

	* Heading 2

	** Sub-Heading 2.1

	   测试下 中文字体 在 emacs 下

	#+BEGIN_SRC R
	  a <- rnorm(100)
	  x <- y^2
	#+END_SRC

	** Sub-Heading 2.2

	* Heading 3

	* A very interesting slide
	  :PROPERTIES:
	  :reveal_data_state: soothe
	  :END:

	This slide is interesting because I am a geek :)

	- bullet points can be added in moderation
	- dont get too carried away with them
