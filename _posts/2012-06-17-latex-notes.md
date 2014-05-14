---
layout: post
title: "latex notes"
description: ""
category:
tags: [latex]
Time-stamp: "liuminzhao 05/05/2014 14:31:52"
---
{% include JB/setup %}

LaTeX notes
==========

# side by side figures #

	\begin{tabular}{cc}
	\begin{minipage}
 		fjsdajfl
 	\end{minipage}

 	\begin{minipage}
 		fasfd
 	\end{minipage}
	\end{tabular}

## Use `subcaption`

	\begin{figure}[ht]
	\centering
	\begin{subfigure}{.5\textwidth}
    \includegraphics[width=1\linewidth]{diffquantiley1.png}
	\caption{Scatter plot of $Y_1$ and fitted quantile lines}
	\end{subfigure}%
	\begin{subfigure}{.5\textwidth}
    \includegraphics[width = 1\linewidth]{diffquantiley2.png}
	\caption{Scatter plot of marginal $Y_2$ and fitted quantile lines}
	\end{subfigure}
	\end{figure}

The `%` after `subfigure` is important to have side by side figures.

## `subfigure` package

	\begin{figure}
	\hfill
	\subfigure[Title A]{\includegraphics[width=5cm]{img1}}
	\hfill
	\subfigure[Title B]{\includegraphics[width=5cm]{img2}}
	\hfill
	\caption{Title for both}
	\end{figure}

## `minipage`

	\begin{figure}
	\centering
	\begin{minipage}{.5\textwidth}
	\centering
	\includegraphics[width=.4\linewidth]{image1}
	\captionof{figure}{A figure}
	\label{fig:test1}
	\end{minipage}%
	\begin{minipage}{.5\textwidth}
	\centering
	\includegraphics[width=.4\linewidth]{image1}
	\captionof{figure}{Another figure}
	\label{fig:test2}
	\end{minipage}
	\end{figure}

[refer](http://tex.stackexchange.com/questions/37581/latex-figures-side-by-side)

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

## underline on journals ##

It is because the package `ulem` making `emph` to have underlines.

# Latexdiff #

	latexdiff old.tex new.tex > diff.tex

# latexdiff with Git #

<http://tex.stackexchange.com/questions/1325/using-latexdiff-with-git>

<http://www.carlboettiger.info/wordpress/archives/3804>

1. create git-latexdiff in `~/bin/` and move to `/usr/local/bin`.
2. update `~/.gitconfig`

		[difftool.latex]
		cmd = git-latexdiff "$LOCAL" "$REMOTE"
		[difftool]
		prompt = false
		[alias]
		ldiff = difftool -t latex

3. usage

		git ldiff HEAD
		git ldiff file
		git ldiff --cached file

A python script: <http://www.numbertheory.nl/2012/02/09/scm-latexdiff-a-python-script-to-calculate-diffs-for-tex-files-in-git-or-mercurial-repositories/>

Not work with sub directory:

	scm-latexdiff local:draft/qrmissingpaper.tex 0dfbe:draft/qrmissingpaper.tex

To work with bibtex: move `qr-missing-reference.bib` to root directory

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

# Subfiles #

<http://tex.stackexchange.com/questions/11311/how-to-include-a-document-into-another-document/11318#11318>

Try `standalone`, or `subfiles` packages.

For `standalone`:

	% main.tex
	\documentclass{article}
	\usepackage{standalone}
	\begin{document}
	\include{B}
	\end{document}

	% B.tex
	\documentclass{article}
	\begin{document}
	...
	\end{document}

## include  and input ##

Input just copy and paste.

## include break page ##

Use `newclude` package and use `\include*{section}`.

## Multiple files ##

Put the following at the end of master file:

	%%% Local Variables:
	%%% mode: latex
	%%% TeX-master: "dissertation"
	%%% End:

or `C-c _`, then `ref` will automatically scan other sub files.


# Table #

## Scale Table to fit on one page ##

Put `\tabcolsep = 0.11cm` before `\begin{tabular}`.

# Subfiles #

	% Main.tex
	% Preamble
	\usepackage{subfiles}
	% More preamble
	\begin{document}
	\subfile{Methods}
	\subfile{AnotherSection}
	\subfile{OtherStuff}
	\end{document}

	% Methods.tex
	\documentclass[Main.tex]{subfiles}
	\begin{document}
	\section{Methods}
	\end{document}

For bibtex, one solution from [here](http://www.latex-community.org/forum/viewtopic.php?f=50&t=10320)

	\documentclass[...]{...}
	\usepackage{natbib}
	\usepackage{subfiles}
	...
	\def\biblio{\bibliographystyle{plainnat}\bibliography{bibliography}}
	\begin{document}
	\def\biblio{}
	...
	\subfile{chapter\_1}
	\subfile{chapter\_2}
	...
	\bibliographystyle{plainnat}
	\bibliography{bibliography}
	\end{document}

In chapter tex file:

	\documentclass[main]{subfiles}
	\begin{document}
	...
	\biblio
	\end{document}

# Bibtex #

Where to get correct bibtex:

go to <http://www.ams.org/mathscinet/index.html>,

then clipboard, then export to bibtex together.

# landscape #

## Whole paper ##

	\usepackage[landscape]{geometry}

## single page ##

	\usepackage{lscape}
	\begin{landscape}
	\end{landscape}

## single page with pdf viewer support ##

	\usepackage{pdflscape}
	\begin{landscape}
	\end{landscape}

# size #

	\tiny
	\scriptsize
	\footnotesize
	\small
	\normalsize
	\large
	\Large
	\LARGE
	\huge
	\Huge

# double spacing #

	\linespread{1.6}

or

	\usepackage[doublespacing]{setspace}

in preamble

# bst, cls, sty #

* bst: reference style
* cls: document class
* sty: generic functions, package

# Others #

	\text -> \mbox
	\bm -> \bmath

# Mathjax #

	\iint

## Fonts ##

	\mathbb
	\mathbf
	\mathtt
	\mathrm
	\mathcal
	\mathscr


# Figure position #

Prefer `[!htbp]`

# PDF figure

	\includegraphics[page=..,trim=...,clip]{foo}

for parts of the page

# Comment #

	% \newcommand{\comment}[1]{}  %comment not showed
	\newcommand{\comment}[1]
	{\par {\bfseries \color{blue} #1 \par}} %comment showed
