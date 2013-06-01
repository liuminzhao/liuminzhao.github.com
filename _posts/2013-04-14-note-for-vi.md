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
8. `NG`: move to N-th line


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
	dd: delete current line, and copy to clipboard
	yy: copy current line (ddP)

# Repeat #

	.
	N<cmd> : repeat N times

# Save/Open #

	:w: save
	:q! : quit without saving 
	:q : quit
	:wq
	:e <path> : open file

# undo and redo #

	u: undo
	C-r: redo
	
# Help #

	:help

# Insert Mode #

	a: after cursor
	o: new line
	O: new line before current line
	cw: replace word

# Auto Completion #

	C-n
	C-p

# Macro #

	qa: record to a
	@a: replay a
	@@: replay latest macro
	qaYp<C-a>q : q stop record

# Reference #

1. <http://www.openvim.com/tutorial.html>
2. <http://coolshell.cn/articles/5426.html>
