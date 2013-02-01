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
