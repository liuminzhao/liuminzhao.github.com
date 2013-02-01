---
layout: post
title: "tmux notes"
description: ""
category: 
tags: [tmux]
---
{% include JB/setup %}

Tmux Notes
==========

[Reference 1](http://liuerfire.is-programmer.com/posts/32150.html)

[Reference 2](http://hjkl.me/tool/2012/05/31/tmux-how-to.html)


C-b : prefix

1. ? : help
2. c : create
3. 0-9 : # window
4. n : next
5. p : previous
6. | : last
7. t : time
8. o : like emacs
9. tmux attach : reattach
10. , : rename window 

change prefix in `~/.tmux.conf` 

	unbind C-b
	set -g prefix C-q

refresh without reboot tmux:

	prefix :
	:source-file ~/.tmux.conf
