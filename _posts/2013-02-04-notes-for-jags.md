---
layout: post
title: "notes for jags"
description: ""
category: 
tags: [jags]
---
{% include JB/setup %}

# Syntax #

## Model ##

	model {
	for (i in 1:M) {
		y[i] ~ dnorm(mu[z[i]], tauinv[z[i]])
		z[i] ~ dcat(p[])
	}

	# stick-breaking prior
	p[1] <- r[1]
	for (j in 2:(N-1)) {p[j] <- r[j]*(1-r[j-1])*p[j-1]/r[j-1]}
	for (k in 1:(N-1)) {r[k] ~ dbeta(1, alpha)}

	#  sum p
	ps <- sum(p[1:(N-1)])
	p[N] <- 1 - ps

	# baseline
	for (k in 1:N) {
	    mu[k] ~ dnorm(basemu, basetau)
	    tauinv[k] ~ dgamma(3, b)
	}
	basemu ~ dnorm(0, .01)	
	basetau <- pow(sigmaF0, -2)
	sigmaF0 ~ dunif(0, 10)
	b ~ dgamma(0.03, 0.03)

	# DPP parameter prior
	alpha ~ dunif(0.3, 10)
	# alpha  <- 1
	}

saved in `example.bug`

## R ##

	library('rjags')
	library('coda)
	jags <- jags.model('example1.bug',
		data = list('x' = x,
		'N' = N),
		n.chains = 4,
		n.adapt = 100)
 
	update(jags, 1000)
 
	jags.samples(jags,
             c('mu', 'tau'),
             1000)

	output <- coda.samples(model=jags,variable.names=c("basemu", "p","mu", "basetau"), n.iter=10000, thin=1)

	print(summary(output))
	plot(output)

## Convergence ##

	codamenu()
