---
layout: post
title: "emacs notes"
description: ""
category:
tags: [emacs]
Time-stamp: "liuminzhao 07/10/2013 16:06:49"
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
	C-h m # short cut for this major? mode

# Flyspell #

correction:

	M-$

# Zoom #

	C-x C-+
	C-x C--
	(global-set-key [C-mouse-4] 'text-scale-increase)
	(global-set-key [C-mouse-5] 'text-scale-decrease)

# Detect from Terminal #

    (when (display-graphic-p)
	    (your)
		(code))

# Ispell on mac #

    brew install ispell
	(setq ispell-program-name "/path/to/ispell")

# searching for program no such file #

Use `homebrew`, then

    (setq exec-path (append exec-path '("/usr/local/bin")))

# /bin/sh: pdflatex: command not found #

`M-x getenv` for `PATH` did not show `/usr/texbin`,

    (getenv "PATH")
	(setenv "PATH"
	(concat
	"/usr/texbin" ":"

	(getenv "PATH")))

# Org-mode #

Schedule time: `C-c C-s`,

     3-2-5         ⇒ 2003-02-05
     2/5/3         ⇒ 2003-02-05
     14            ⇒ 2006-06-14
     12            ⇒ 2006-07-12
     2/5           ⇒ 2007-02-05
     Fri           ⇒ nearest Friday after the default date
     sep 15        ⇒ 2006-09-15
     feb 15        ⇒ 2007-02-15
     sep 12 9      ⇒ 2009-09-12
     12:45         ⇒ 2006-06-13 12:45
     22 sept 0:34  ⇒ 2006-09-22 0:34
     w4            ⇒ ISO week for of the current year 2006
     2012 w4 fri   ⇒ Friday of ISO week 4 in 2012
     2012-w04-5    ⇒ Same as above

# yasnippet #

	`(my-insert-date)`

# Time-stamp #

work in the first **8** lines of the file

Two formats:

	Time-stamp: <>
	Time-stamp: " "

Pattern:

	"8/Time-stamp:[ \t]+\\\\?[\"<]+%:y-%02m-%02d %02H:%02M:%02S %u\\\\?[\">]"

reference: <http://emacs-fu.blogspot.com/2008/12/automatic-timestamps.html>

# Multi-cursor #

insert increasing number: `C-1 M-x mc/insert-numbers`

# Outline-Minor-Mode #

<http://www.emacswiki.org/emacs/OutlineMinorMode>

	; Outline-minor-mode key map
	(define-prefix-command 'cm-map nil "Outline-")
	; HIDE
	(define-key cm-map "q" 'hide-sublevels)    ; Hide everything but the top-level headings
	(define-key cm-map "t" 'hide-body)         ; Hide everything but headings (all body lines)
	(define-key cm-map "o" 'hide-other)        ; Hide other branches
	(define-key cm-map "c" 'hide-entry)        ; Hide this entry's body
	(define-key cm-map "l" 'hide-leaves)       ; Hide body lines in this entry and sub-entries
	(define-key cm-map "d" 'hide-subtree)      ; Hide everything in this entry and sub-entries
	; SHOW
	(define-key cm-map "a" 'show-all)          ; Show (expand) everything
	(define-key cm-map "e" 'show-entry)        ; Show this heading's body
	(define-key cm-map "i" 'show-children)     ; Show this heading's immediate child sub-headings
	(define-key cm-map "k" 'show-branches)     ; Show all sub-headings under this heading
	(define-key cm-map "s" 'show-subtree)      ; Show (expand) everything in this heading & below
	; MOVE
	(define-key cm-map "u" 'outline-up-heading)                ; Up
	(define-key cm-map "n" 'outline-next-visible-heading)      ; Next
	(define-key cm-map "p" 'outline-previous-visible-heading)  ; Previous
	(define-key cm-map "f" 'outline-forward-same-level)        ; Forward - same level
	(define-key cm-map "b" 'outline-backward-same-level)       ; Backward - same level
	(global-set-key "\M-o" cm-map)
