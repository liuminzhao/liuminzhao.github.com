---
layout: post
title: "statcomp2 notes"
description: ""
category: 
---
{% include JB/setup %}

Stat Comp at JSPH
==========

# Unix/Linux #

	- `chmod -w filename` , ur self 

	- `grep' : find text in file 

# Emacs #

	- `C-M-s ` : regexp search
	- `C-x d ` : dir mode 
	- `M-5 c` : ccccc
	- `M-x tetris ` 
	
    - new command
		- `\newcommand{}{}`
		- `\newcommand{}[2] ...#1`

# R #

	- `R BATCH inputfile outputfile &`
	- `system("ls")`
	- `break` : jump out of loop
	- `next`: move to next loop
	- `lapply`: apply FUN to each element in list 
	- `sapply` : same way, but return a vector or matrix if possible

# Coding Practices #

	- start with WHO, WHEN , WHAT, HOW 
	- end with 'end of myfile.R'
	
	- function star with WHAT,
	- INPUT
	- OUTPUT 
	- plan to spend 1/4 of your time commenting
	
# [ R by Roger](http://www.biostat.jhsph.edu/~bcaffo/statcomp/files/Rother.pdf) #
	
	- S3 , old style class (quick and dirty)
	- S4, new style class (encourageed to use)
	- mean.default 
	- your own methods:
		- print/show
		- summary
		- plot 
	- example:
	    - setClass("polygon", representation(x="numeric", y="numeric"))
		- setMethod("plot","polygon", function(x,y).....)
		- p <- new("polygon", x=c(1,2,3,4),y=c(1,2,3,4))
		- plot(p)

# [R Debug](http://www.biostat.jhsph.edu/~bcaffo/statcomp/files/R-debug-tools.pdf) #

- *traceback*
- stepping through with *debug* 

	    debug(function)
		undebug(function)

	    Browse[2]> mu
		[1] 1
		Browse[2]> n
		debug at #4: ss <- sum(d2)
		Browse[2]> d2
		[1] 4

        n : next
        c : rest of the function w/o stopping
        Q : quit
        where : where
	    ls()
	  
- *browser()* , put inside the function
- *trace*
- *trace* with *recover*
- `options(error=recover)`

- *cat()* is more flexible than *print()*
	  
# R OO #

- *methods(summary)*
- *getS3method()*
- *getAnywhere()*

        class(x) <- "roger"
		print.roger <- function(x, ...) cat(..fasmf)

# [R Package](http://www.biostat.jhsph.edu/~bcaffo/statcomp/files/rpacks.pdf) #   

- R
- man
- data
- demo
- exec : code for Perl and other system tools
- inst : doc  vignette
- src
- tests : R check 

- DESCRIPTION

# [C](http://www.biostat.jhsph.edu/~bcaffo/statcomp/files/cprog1_ho.pdf) #
  
# [.Call](http://www.biostat.jhsph.edu/~bcaffo/statcomp/files/dotCall.pdf) #

- very useful in matrix : 

        allocMatrix(afsd, I, J)
