---
layout: post
title: "linux notes"
description: ""
category: 
tags: [linux]
---
{% include JB/setup %}

# grep #

[reference](http://bbs.chinaunix.net/thread-692640-1-1.html)

all file contains 'boss'

	grep -l 'boss' * 

show line number 

	grep -n 'boss' file
	
# Diff #

Compare 2 folders:

	diff -bur folder1/ folder2/

[xahlee](http://xahlee.info/UnixResource_dir/unix_shell_text_processing.html)

# Regex #

## Syntax ##

	. : any 
	^: start 
	$: end
	[]: indicate a set of char
	\d == [0-9]
	\D = [^0-9] ; non digit
	\s : any whitespace
	\S: any non whitespace
	\w: [a-zA-Z0-9_]
	\W : [^a-zA-Z0-9_]

## Repeating ##

	*: zero or more {0,}
	+: at least one {1,}
	? : once or none {0,1}
	{m,n}: m-n times
