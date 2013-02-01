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
