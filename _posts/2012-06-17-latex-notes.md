---
layout: post
title: "latex notes"
description: ""
category:
tags: [latex]
---
{% include JB/setup %}

LaTeX notes
==========

# parallel picture #

	  \begin{tabular}{cc}
 	  \begin{minipage}
 	  fjsdajfl
 	  \end{minipage}

 	  \begin{minipage}
 	  fasfd
 	  \end{minipage}
	  \end{tabular}

# Number #

Number a group of equations:

	\begin{equation}
		\begin{aligned}
			w^T x_i + b &\geq 1-\xi_i &\text{ if }& y_i=1,  \\
			w^T x_i + b &\leq -1+\xi_i & \text{ if } &y_i=-1,
		\end{aligned}
	\end{equation}

# Citation #

* remove aux and bbl file to refresh
* change bib file encoding with uft-8 by

    	C-x RET f utf-8 RET

* Code:

	    \usepackage{natbib}
	    \bibliographystyle{plainnat}
		\bibliography{\filename}

* do not use the same file name for bib file

# Latexdiff #

	latexdiff old.tex new.tex > diff.tex

# latexdiff with Git #

<http://tex.stackexchange.com/questions/1325/using-latexdiff-with-git>

<http://www.carlboettiger.info/wordpress/archives/3804>

1. create git-latexdiff.sh in `~/bin/`
2. update `~/.gitconfig`

	    [difftool.latex]
        cmd = git-latexdiff "$LOCAL" "$REMOTE"
		[difftool]
        prompt = false
		[alias]
        ldiff = difftool -t latex

3. usage

	    git latexdiff HEAD
		git latexdiff file
		git latexdiff --cached file

# Emacs #

## Doc ##

doc-view-mode with auto-revert-mode ?

## Font ##

`C-c C-f` +

    C-e : \emph
	C-b : bold
	C-c : textsc
	C-i : textit
	C-t : texttt

`C-u C-c C-f C-b` : change the current font to ...

## format ##

    C-c C-q C-s
	M-q

## Reftex ##

    C-c = : reftex toc
	C-c [ : insert citation
	C-c ( : label
	C-c ) : add reference  = refe

## Environments ##

    C-c ] : close current environment

## Preview under Mac ##

<http://tex.stackexchange.com/questions/28458/preview-latex-in-emacs-auctex-empty-boxes>

    Preview -> Customize -> Browse Options -> Preview GS -> options -> del-dSAFER

`C-x C-s` to save and reload.

## Latex-pretty-symbols ##

    M-x latex-unicode-simplified

<https://bitbucket.org/mortiferus/latex-pretty-symbols.el>

# Tips #

## Using LaTeX to Split PDF Files ##

Suppose your source pdf is source.pdf, you wanna draw the 2nd and 4th page from that, by

    \usepackage{pdfpages}
	\includepdf[page={2,4}]{source}

`pdflatex` -> voila, here you are.



# Titlepage and Cover #

0. <http://blog.sina.com.cn/s/blog_5e16f1770102epls.html>
1. <http://tex.stackexchange.com/questions/17579/how-can-i-design-a-book-cover>
2. <http://tug.org/PSTricks/main.cgi?file=Examples/Logos/logos>
3. <http://www.texample.net/tikz/examples/pgf2-titlepage/>
4. <http://www.ctan.org/tex-archive/info/latex-samples/TitlePages>

# Break Long Equation #

1. <http://stackoverflow.com/questions/1578127/how-do-i-break-a-long-equation-over-lines>
2. <http://tex.stackexchange.com/questions/22573/how-can-i-tell-auctex-that-breqn-is-a-math-environment>

    \documentclass{article}
	\usepackage{breqn}
	\begin{document}
	\begin{dmath}
	f(n)-f(0) = A(n)-B(n)-C(n)-D(n)\cdot d-\left(A(0)-B(0)-C(0)-D(0)\cdot d\right)
          = A(n)-0-X-D(n)\cdot d-\left(0-0-0-0\right)
          = A(n)-X-D(n)\cdot d
    \end{dmath}
	\end{document}

In order to turn on math mode in `dmath` environment:

    (add-hook 'LaTeX-mode-hook 'add-my-latex-environments)
	(defun add-my-latex-environments ()
	(LaTeX-add-environments
    '("dmath" LaTeX-env-label)))
    ;; Code I added to make syntax highlighting work in Auctex
    (custom-set-variables
	'(font-latex-math-environments (quote
    ("display" "displaymath" "equation" "eqnarray" "gather" "multline"
    "align" "alignat" "xalignat" "dmath")))
	'(TeX-insert-braces nil)) ;;Stops putting {} on argumentless commands to "save" whitespace
	;; Additionally, reftex code to recognize this environment as an equation
	(setq reftex-label-alist
	'(("dmath" ?e nil nil t)))
