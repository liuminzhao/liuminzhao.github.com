---
layout: post
title: "notes for jags"
description: ""
category:
tags: [jags]
---
{% include JB/setup %}

# Procedure

1. Model
2. Compilation
3. Initial
4. Adapt and burn in
5. monitoring

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

## Data and init

	data <- list(x = x, y = y)
	init <- list(beta = 0, tau = 1)
	jags <- jags.model(..., inits = init, data = data,
		n.chain = 3, n.adapt = 100)

## Monitor

	par = c('alpha', 'beta')
	samp = coda.sample(jags, par, n.iter = 20000)
	plot(samp)
	summary(samp)

### window

	burn.in = 1000
	summary(window(samp, start = burn.in))

## Convergence ##

	codamenu()

	gelman.diag(samp)
	gelman.plot(samp)


## prediction

	round(summary(window(samps[, paste("y[", 1:25, "]",
	sep = "")], start = burn.in))$quantiles[, c(3, 1, 5)], 2)

## Useful functions

### Categorical

	y ~ dcat(p[]) # 1 ~ n

### multinomial

	y[i, 1:3] ~ dmulti(q[], n[i]) # (1,2,n-3)
	n[i] = sum(y[i,])

### Dirichlet

	q[1:3] ~ ddirch(alpha[])
	for (k in 1:3){alpha[k] <- 1}



# Stochastic vs. Deterministic Nodes

- Observed data must correspond to stochastic nodes
- All constants like N must be known at compile-time
- Deterministic nodes are nothing more than shorthand
  A deterministic node can always be optimized out!
- Stochastic nodes are the essence of the program

# Syntax #

## Truncated and censored ##

	T(,): a priori restriction
	I(,): a posteriori restriction

## Others ##

- BUGS uses precision rather than variance
- power: `pow(x, 2)`

## Mixture Normal ##

	Y[i] ~ dnormmix(mu[], tau[], p[])

# Reference #

1. <https://github.com/johnmyleswhite/JAGSIntro/blob/master/slides.md>
2. <http://w3.jouy.inra.fr/unites/miaj/public/nosdoc/rap2012-5.pdf>
3. <http://ftp.iinet.net.au/pub/FreeBSD/distfiles/mcmc-jags/jags_user_manual.pdf>
4. <http://bendixcarstensen.com/Bayes/Cph-2012/pracs.pdf>
5. <http://sousalobo.com/aom2011pdw/JAGS_tutorial_Lobo.pdf>
6. <http://jackman.stanford.edu/classes/BASS/ch8.pdf>
7. <http://www.math.helsinki.fi/openbugs/IceBUGS/Presentations/PlummerIceBUGS.pdf>
8. <http://www.mrc-bsu.cam.ac.uk/bugs/faqs/contents.shtml>
9. <http://blue.for.msu.edu/CSTAT_13/exercises/exercise-1/ex-1.pdf>
10. <http://polisci2.ucsd.edu/cfariss/HumanRightsScores/Code.html>
11. <http://www.columbia.edu/~cjd11/charles_dimaggio/DIRE/styled-4/styled-11/code-8/>
12. <http://darrenjw.wordpress.com/tag/tutorial/>
13. <http://cddesjardins.files.wordpress.com/2010/04/8290_mcmc2.pdf>
14. [winbugs manual](http://www.mrc-bsu.cam.ac.uk/bugs/winbugs/manual14.pdf)
