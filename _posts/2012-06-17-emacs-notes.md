---
layout: post
title: "emacs notes"
description: ""
category: 
tags: [emacs]
---
{% include JB/setup %}

Emacs Notes
==========

# No window mode #

- set mark : C-2 ; C-@
- backward-kill-word: C-M-h , M-backspace 

# Chinese input , Ubuntu 12.04 #

    > sudo locale-gen zh_CN.UTF-8
	> LC_CTYPE="zh_CN.UTF-8" emacs
	> sudo gedit /etc/environment
	> add 
	> LC_CTYPE="zh_CN.UTF-8"

# Comments #

## ess roxygen ##

    C-c C-o 

## Doxymacs ##

<http://emacser.com/doxymacs.htm> 

# Font size change #

	C-x C-+ / - 
	
# Set Mark #
 
	C-2
	C-S-Space

# put backup file together #

	(setq backup-directory-alist
      '((".*" . "~/.emacs.d/var/backups")))

# encoding #

when I save a file with encoding `utf-16`, it is not recognized by `git`, so need to change the encoding of the existing file:

	C-x RET f utf-8 RET

# Indent #

	indent-regidly
	C-u 4 C-x TAB
	
[Reference](http://ruslanspivak.com/2011/04/28/how-to-indent-a-block-of-text-in-emacs/)

# rectangle command #

select the region starting and ending with the left top and bottom right of the rectangle

	C-x r k # kill 
	C-x r y # paste

reference: <http://www.gnu.org/software/emacs/manual/html_node/emacs/Rectangles.html> 

# Macro # 

	C-x (
	C-x )
	C-x e : repeat last macro
	C-u 10 C-x e : repeat last 10 times
	
# Cua Mode # 

	M-x cua-mode
	C-ENTER : mark 
	ENTER: mark
	M-n : insert number 
	
# Move #

	M-x forward-whitespace
	M-< # begin
	M-> # end

# Scratch #

	C-j : eval line
	C-x b *scratch* RET : open scratch 
	M-x text-mode 
	M-x apropos-command -mode$ RET : search for mode 

# Help #

	C-h f # function
	C-h v # variable
	C-h w # keyboard

# Flyspell #

correction: 

	M-$ 
	
