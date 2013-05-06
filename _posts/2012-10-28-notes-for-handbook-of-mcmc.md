---
layout: post
title: "Notes for Handbook of MCMC"
description: ""
category: 
tags: [book]
---
{% include JB/setup %}

Notes on Handbook of MCMC
==========

Authors(Editors): Steve Brooks, Andrew Gelman, Galin Jones, Xiao-li Meng

1. Check Mixing trace plot and lag plot (`acf`)

2. Monte Carlo standard error (MCSE) is $\hat{\sigma}/ \sqrt{n}$ , where 

$$
\sigma = \frac{1}{n} \sum\_i^n (X\_i - \mu)^2
$$

3. Multistart 

4. `if (logr >= 0 || unif < exp(logr))` 

5. random walk, `y = x + e` , where `e` is symmetric distributed. 

6. recommended optimal acceptance rate `0.234` for `d > 1`. (0.1 - 0.6) is fine. For `d = 1`, take `0.44`. 

7. For `mcmc` R package, check mixing : 

	    plot(ts(out$batch))
     	acf(out$batch)
	
	lag 25 is sufficient to make the lag under `0.2`. 

	    vignette("demo", package = "mcmc")
	
8. scale is tuning the variance of proposal distribution $$N(0, \sigma^2)$$. 

9. If $\sigma$ is too small, acceptance rate is high, not cover the whole posterior distribution . If $\sigma$ is too large, jumping around, rejecting too much. Not moving. 

10. For Metropolis-within-Gibbs, for every parameter, `d = 1`. The recommended optimal acceptance rate is fine when `d >= 5`. 

11. In Haario et al 2001, adaptive metropolis algorithm recommend the proposal distribution:

	$$N(Y\_{n-1}, 2.38^{2} / d \Sigma)$$
	
	where $\Sigma$ is the sample var-cov matrix. 

12. `Tuning` and adaptive metropolis within gibbs . In Robert and Rosenthal, 2005, monitor every 50 samples, make $\sigma \pm \delta(n)$ if acceptance rate $\neq 0.44$ , where $\delta(n) \to 0$ , one recommended is 

    $$\delta(n) = min(0.01, 1/\sqrt{n})$$

13. Inference: 

	a. 3 and more parallel chains

	b. discard first half (conservative)

	c. mix after convergence

14. thin

15. when reporting $\theta_{\pi}$, MCSE should be included. 

# Notes from Steven Walker Lecture #

f(y) = \int f(y|x)f(x)dx

f(y|x) = \int f(y|u)f(u|x)du

If f(y) = h(y)g(y), f(y, u) = I(u < h(y))g(y),

f(u|y) = h(y)^-1 I(u< h(y))

f(y|u) \propto g(y)I(u<h(y))

Instead of starting from beginning, M-H/gibbs make use of good samples, find new
samples around previous one. Gibbs goes to stationary distribution by MC

\pi(mu\_n+1, lambda\_n+1) = \int \int pi(mu\_n+1|lambda\_n+1) pi(lambda\_n+1|mu\_n) pi(
mu\_n, lambda\_n) dmu\_n dlambda\_n

q(y|x) is the proposal density, if f(y|x) is the transition density

    f(x)f(y|x) = f(y)f(x|y)

then

    f(y) = \int f(y|x)f(x) dx


## Methopolis Hasting ##

set the transition density :

    f(y|x) = r(x) [a(y, x)q(y|x) /r(x)] + (1 - r(x)) I(y = x)

simplest choice of $\alpha$ is

    a(y, x) = min{ 1, q(x|y)f(y)/(q(y|x)f(x))}

## slice sampling ##

can be generalized to `f(x)= g(x)h(x)`
