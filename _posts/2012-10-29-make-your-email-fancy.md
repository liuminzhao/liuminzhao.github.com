---
layout: post
title: "make your email fancy"
description: ""
category: 
tags: [email, R, openssl]
---
{% include JB/setup %}

One way to make your email fancy 
==========

First let me show the screenshot:

	echo pyzmysnlwjacmwypvhjm | tr mzhvasypwjcnl muc.@nilaogzh

idea is  from <http://lhzhang.com/about.html> . I made a R code but not satisfied since it is too complicated. I believe there is simpler way to do that. 

<script src="https://gist.github.com/3971075.js"></script>

Inspired by [roowe](http://www.iroowe.com/me_guestbook/), another example is by `openssl`:

	cho bGl1bWluemhhb0BnbWFpbC5jb20K | openssl base64 -d
	
Notes for `openssl` :

To decode from Base64:

	openssl base64 -d -in <infile> -out <outfile>
	
Conversely, to encode to Base64:

	openssl base64 -in <infile> -out <outfile>
	
	$ echo "encode me" | openssl enc -base64
	ZW5jb2RlIG1lCg==

[reference1](http://hints.macworld.com/article.php?story=20030721010526390)

[reference2](http://www.madboa.com/geek/openssl/#encrypt-base64)
