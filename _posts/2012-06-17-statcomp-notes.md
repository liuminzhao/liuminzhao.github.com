---
layout: post
title: "statcomp notes"
description: ""
category: 
tags: []
---
{% include JB/setup %}

[Advanced statistical computing Notes ](http://www.biostat.wisc.edu/~kbroman/teaching/statcomp/index.html)
==========
# Pre #

	C: speed
	perl: data manipulation
	R: analyses and graphics

## C ##

[C](http://www.biostat.wisc.edu/~kbroman/Cintro/)

## Perl ##

    #!/usr/bin/perl -w

**w** for warning

    chmod +x program.pl
    #!/usr/bin/perl -w
    print("Hello, world!\n");

### more complicated example ###

[convert](http://www.biostat.wisc.edu/~kbroman/perlintro/convert.html)

`open(IN, $mfile)` or die

## R ##

### Ch 1 : Intro 

### Ch 2 : R 

### Ch 3 : random number generation 

    #include <R.h>
	GetRNGstate();
	PutRNGstate();
	double unif_rand();
	double norm_rand();
	double exp_rand();
	double r****();

	/usr/local/lib/R/include/R.h
	/usr/local/lib/R/include/R_ext/Mathlib.h
	RHOME/src/main/RNG.c
	RHOME/src/nmath/snorm.c
	RHOME/src/nmath/sexp.c

# Ch 4: permutation test, and bootstrap  #

## Permutation test ##

## Parametric Bootstrap ##

## Nonparametric Bootstrap ##

## Bootstarp in regression  ##

# Ch5 : Numerical Linear Algebra #

# Ch 6: EM  #

- Standard errors
- Maximizing 
- Slow convergence

# Ch 7: Newton-Raphson, Fisher Scoring  #

# Ch 8: Numerical Integration #

- don't use `h*f(x)` in reality 
- Error O(1/N^2)
	
## Gaussian Quadrature  ##

# Ch 9 : MCMC #

- burn in : drop the first M steps, Gelman, drop the first half 
- keep only every kth sample: gelman, keep every sample 
- want steps to be big
- don't want to reject too often
- data augmentation (EM) can be helpful 
- reject 44% when p=1, 23% when p>5 

# Ch 10: Remarks #

- against using Fortran
- use C and perl 
