---
layout: post
title: "Octave Notes"
description: ""
category: 
tags: [octave]
---
{% include JB/setup %}

Octave Notes from Coursera online Machine Learning Course
==========

## Basic Operation

1. `~=` : not equal
2. `2^6`
3. `&&` and `||` or
4. `%` comment
5. `PS1('>> ')` change prompt
6. `;` not show results
7. `a=3`
8. `a='hi'`
9. pi
10. `disp(a)`
11. `sprintf('fsdf %0.2f', a)` , string print
12.  `format long/short`

## Math

	std
	sqrt
	log
	exp
	sin, cos

## Matrix/Vector 

1. `A=[1 2;3 4;5 6]`
2. `v=1:0.1:2` or `v=1:6`
3. `ones`, `zeros`, `rand`, `randn` for random normal, `eye`
4. `sqrt`
5. `hist(w, bins=50)`
6. `help`
7. `A(2,:)`
8. `A([1 3],:)` : 1st, 3rd row
9. `A=[A, [1;2;3]]` : append column
10. `size(A)` and `size(A,1)`
11. `length(v)`
12. `C=[A B]`
13. `C=[A;B]`

## File/Imput/Save 

1. `pwd` 
2. `cd`
3. `ls`
4. `load ***.dat` , `load('***.dat')`
5. `who` , `whos`, =ls
6. `save hello.txt v`

## Data/Matrix

- `A*C`
- `A .* C` and `A .^ 2` ; elementwise
- abs, log, exp
- transpose `A'`
- max(a), max(A,[],1), column max, max(A,[],2), row max
- `[val, ind] = max(a)`
- `find(a < 3)`
- `magic(3)`
- `[r,c]=find(A>7)`
- `sum, prod, floor, ceil, sum(A,1), pinv, inv`

## Plot

- `plot(x,y,'rx')` : r is color, x marker, '-' for lines, '+', 'o'
- `hold on`
- `xlabel('time')`
- `legend('sin', 'cos')`
- `title('title')`
- `print -dpng 'xxx.png'` : save to png
- `figure(1)`
- `subplot(1,2,1)` 
- `axis([0.5 1 -1 1])`
- `imagesc(A), colorbar, colarmap gray`
- `surf` : 3-d
- `contour` : contour

## Clear

	clear
	clc
	close all

## Loop 

	for i = 1:10,
		statement;
	end;
	
	indices=1:10;
	for i = indices,
	...
	
	while i<=5,
	...
		break;
	end;

	if i<=5,
		...
	elseif ...,
	else
		...
	end;

	2:end

## Function

need to name myfunction.m, and put in the pwd

	function [y1, y2]=myfcn(x)
	y1=...

	addpath('C:fff')

	fmincg

## submit homework

change to homework directory, after you finish, just type

	submit()

# Emacs #

	(autoload 'octave-mode "octave-mod" nil t)
	(setq auto-mode-alist
		(cons '("\\.m$" . octave-mode) auto-mode-alist))
	(add-hook 'octave-mode-hook
	(lambda ()
            (abbrev-mode 1)
            (auto-fill-mode 1)
            (if (eq window-system 'x)
                (font-lock-mode 1))))

	C-c Tab l : exec line
