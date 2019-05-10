---
title: "markdown notes"
description: ''
layout: post
tags: markdown
category: null
---
{% include JB/setup %}

# Cheatsheet

<https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#wiki-tables>

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

	| Trend                     | N                  | A    | M    |
	|---------------------------|--------------------|------|------|
	| N                         | N,N                | N,A  | N,M  |
	| A(additive)               | A,N                | A,A  | A,M  |
	| Ad(additive damped)       | Ad,N               | Ad,A | Ad,M |
	| M(multiplicative)         | M,N                | M,A  | M,M  |
	| Md(multiplicative damped) | Md,N               | Md,A | Md,M |

and can use [Emacs table mode](http://table.sourceforge.net/)

or use **orgtbl-mode**

and use markdown table generator: <http://www.tablesgenerator.com/markdown_tables>



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

# Knitr

For latex, insert 

	<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

For figure caption: use `fig.cap`. Other options can refer [reference](http://kbroman.org/knitr_knutshell/pages/Rmarkdown.html)

# Video

[reference](https://about.gitlab.com/handbook/product/technical-writing/markdown-guide/#images)

## Display videos from YouTube

This method works for YouTube videos and any other embed video within an `<iframe>` tag.

1. Copy the code below and paste it into your markdown file. Leave a blank line above and below it. Do NOT edit the code block (e.g., remove spaces - the video iframe may not render properly)
2. Go the video URL you want to display
3. Click on "Share", then "Embed"
4. Copy the `<iframe>` source (src) URL only, and paste it replacing the src below:

```
<!-- blank line -->
<figure class="video_container">
  <iframe src="https://www.youtube.com/embed/enMumwvLAug" frameborder="0" allowfullscreen="true"> </iframe>
</figure>
<!-- blank line -->
```

## Display local videos (HTML5)

This method works for any video uploaded to somewhere retrievable from the internet from a URL, or from a relative path like path/to/video.mp4.

1. Read through the w3schools HTML5 video guide, or the MDN `<video>` guide.
2. Record or export the video in these three formats to achieve cross-browser and cross-device compatibility: .mp4, .ogg and .webm.
3. Get the URL for your video
4. Choose an image to use as a poster
5. Copy the code below and paste it to your file
6. Replace the src URLs for your video URLs

```
<!-- blank line -->
<figure class="video_container">
  <video controls="true" allowfullscreen="true" poster="path/to/poster_image.png">
    <source src="path/to/video.mp4" type="video/mp4">
    <source src="path/to/video.ogg" type="video/ogg">
    <source src="path/to/video.webm" type="video/webm">
  </video>
</figure>
<!-- blank line -->
```

