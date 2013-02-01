---
layout: post
title: "R Parallel notes"
description: ""
category: 
tags: [R, Parallel]
---
{% include JB/setup %}

R Parallel Notes
==========

# Reference

* R/HPC/luke.pdf
* getttingstartedMC.pdf 
* <http://www.r-bloggers.com/parallel-r-loops-for-windows-and-linux/>
* snow is for cluster
* MC is for one machine , multi-core
* no doMC, mc for GUI


# Material #

* foreach
* doMC
* multicore
* doSNOW
* snow

# Method #

doMC is an interface between foreach and multicore

doNWS and doSNOW use nws and snow respectively

	library(doMC)
	registerDoMC()
	x<- iris[which(iris[,5]!='setosa'),c(1,5)]
	trials<- 10000
	r<- foreach(icount(trials), .combine=cbind) %dopar% {
		ind<- sample(100,100,replace=T)
		result1<- glm(x[ind,2]~x[ind,1],family=binomial(logit))
		coefficients(result1)
	}
	
	options(cores=4)

	foreach(..., .combine, .init, .final=NULL, .inorder=TRUE,
		.multicombine=FALSE, .maxcombine=if (.multicombine) 100 else 2,
		.errorhandling=c('stop', 'remove', 'pass'), .packages=NULL,
		.export=NULL, .noexport=NULL, .verbose=FALSE)
		when(cond)
			e1 %:% e2
			obj %do% ex
			obj %dopar% ex
		times(n)


# Parallel #

	library(parallel) # snow+multicore
	detectCores()
