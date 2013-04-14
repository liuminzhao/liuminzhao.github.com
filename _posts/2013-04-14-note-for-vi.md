---
layout: post
title: "note for vi"
description: ""
category: 
tags: [vi]
---
{% include JB/setup %}

# Mode #

    esc : command
	i : insert 
	v: visual mode
	C-v: visual block
# Move #


    h, j, k, l
	
1. `w`: start of the next word
2. `b`: beginning
3. `e`: end
4. `0`: beginning of the line
5. `$`: end of the line
6. `gg`: beginning of the screen
7. `G`: end of the screen

# Number #

    3w: move forward 3 words
	30i- Esc: insert 30 -
	
# Search #

    f: find
	F: previous
	3fq: 3rd occurance of q
	*: next word under cursor
	#: previous 
	/: search
	n: next
	N: previous
	
# Parentheses #

    %: matching parentheses

# New Line #

    o, O

# Remove and Replace #

    x: current
	X: previous
	r: replace
	d: delete
	p: paste

# Repeat #

    .

# Save #

    :w: save
	:q! : quit without saving 
	:q : quit 
	
# undo and redo #

    u: undo
	C-r: redo
	
# Help #

    :help

# Reference #

1. <http://www.openvim.com/tutorial.html>
