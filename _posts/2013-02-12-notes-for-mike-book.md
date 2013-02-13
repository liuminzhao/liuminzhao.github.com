---
layout: post
title: "notes for mike book"
description: ""
category: 
tags: [longitudinal, stat]
---
{% include JB/setup %}

Notes for Missing Data in Longitudinal Studies by Mike Daniels
==========

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script> 

<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      processEscapes: true
    }
  });
</script>

<script type="text/x-mathjax-config">
    MathJax.Hub.Config({
      tex2jax: {
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre', 'code']
      }
    });
</script>

<script type="text/x-mathjax-config">
    MathJax.Hub.Queue(function() {
        var all = MathJax.Hub.getAllJax(), i;
        for(i=0; i < all.length; i += 1) {
            all[i].SourceElement().parentNode.className += ' has-jax';
        }
    });
</script>

<script type="text/javascript"
   src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

# MTM #

- $logit(\mu_{ij}) = x\beta$
- $\log(\phi) = \delta + y\gamma_{j}$

# Misc #

- missing assumption can not be verified
- when posterior is not closed form, use sample from posterior
- use diffuse prior
- prior can be improper, but posterior should be proper or *just proper*
- in complete data, variance parameter is ancillary but important for efficiency. In missing data scenario, variance parameter is important for consistency.
- For missing data, Bayesian allow assumptions about nonidentified parameters and uncertainty about the assumption. While frequentist uses fixed value or constraints. 

# Some Recommendation #

- $\sigma$: truncated uniform or folded normal
- $\tau$ : uniform shrinkage
- $\Sigma$ : flat prior , reference prior, just proper wishart. Since improper prior can not be used in Winbugs, so use just proper priors.

# Posterior Consistency #

$p(\theta|y) \to \theta_{0}$ which is a point mass (ture value) as $n \to \infty$ the sample size goes to infinity


# Sampling #

## Gibbs ##

- each can be conjugate
- If not random walk, optimal acceptance rate could be 100%
- Choose normal approximation or Laplace approximation for full conditional distribution

Recommendation:

1. random walk for 1 parameter and which is not expensive
2. when not expensive, can be applied on full distribution
3. works on heavy tailed well 

## Data Augmentation ##

What we want is $p(\theta|y)$, use auxiliary variable z:

1. $p(z|\theta, y)$
2. $p(\theta| z, y)$

- If there is latent variable, it suit better (probit, random effect)
- often used for multivariate t distribution

# Inference #

After getting samples, the problem is how to use samples to get inference

1. discard K (burn-in) 
2. multiple chain
3. autocorrelated (lag k) (lag 10 is fine)
4. block gibbs or non-random walk used to speed mixing by reducing autocorrelation
5. thinning, but inefficient
6. batching is more efficient

# Model Selection #

## DIC ##

Drawbacks:

1. likelihood based
2. not invariant
3. no closed likelihood

## PPL ##

# Nonparametric  #

- $p(y|\theta)$
- $\theta \sim G(\theta)$
- $G \sim DP(G_{0}, \alpha)$

$\alpha$ controls how similar nonparametric G is close to $G_{0}$. $\alpha \to \infty \rightarrow G \to G_{0}$.

- can check random effect distribution

# Missing #

- Full data : $p(y, r | \theta, \omega)$
- Full data response model : $p(y|x, \theta)$

## MAR ##

- For monotone dropout, MAR is equivalent to $P(U=j|Y) = P(U=j|Y_{j})$, which means the hazard is only relevant to previous observed one. 

- MAR + Ignorability goes to simplification

- By $p(y_{2}|y_{1}, r= 0, \theta) = P(y_{2}|y_{1}, r = 1, \theta)$, it is easy to impute data and then model regression from completed data

- MTM not suitable
- Example 5.9: MAR can not assure ignorability 

## MNAR (Non ignorable)##

1. use unvarified parametric assumption
2. use informative prior

### Selection Model ###

$y, r = p(y)p(r|y)$

Pros:

1. $y|x$
2. $r|y$
3. when monotone dropout, $r|y$ is hazard function

Cons:

1. sensitive to model specification
2. sometimes identification problem

Example:

$g(\pi_{i}) = \phi_{0} + \phi_{1}y_{1} + \phi_{2}y_{2}$

if $\phi_{2} = 0$ is equivalent to MAR

cons:

1. assumptions can not be verified
2. potential sensitivity problem

### Mixture Model ###

$p(y, r) = p(y|r,x,\omega)p(r|x, \omega)$

cons:

- $y|r$ is sensible

$p(y_{2},y_{1}|r, \alpha) = p(y_{2}|y_{1}, r, \alpha_{E})p(y_{1}|r, \alpha_{o})$

In general, $\alpha_{E}$ can not fully identified from the data alone. 

$\alpha_{E}, \alpha_{O}$ may overlap. So assume

$\alpha_{E} = (\alpha_{EI},\alpha_{NI}$

where $\alpha_{NI}$ can be used to do sensitivity analysis, or use informative prior

Example: bivariate normal

cons:

- when dimension of observations goes up, number of $\alpha_{NI}$ goes up too

### Shared Parameter Model ###

# Ignorability #

1. $p(ymis|yobs, \theta)$ using Data augmentation
2. $p(\theta|y)$ using gibbs sampler

Strongly rely on the assumption of $p(y|\theta)$

Misspecification leads to inconsistency. 

GARP/IV

- for ignorable data, only need to specify $p(y|\omega)$
- for non-ignorable: $p(y, r|\omega)$ is mandatory

# NONIGNORABLE #

- sensitivity parameter and sensitivity analysis
- informative prior
- not identifiable from observed data but when they are fixed, remainder is identified.

## Selection Model ##

parametric model are not suitable to sensitivity analysis

### Semiparametric Selection Model ###

- parametric form for $r|y$
- non or semi-parametric form for $y|\omega$ or $y,r|\omega$
- informative prior on $\phi_{2}$

pros:

1. specify $r|y, y|\omega$, and $\beta$ explicit

cons:

1. sensitivity analysis

## Mixture Model ##

$p(y|\omega,x) = \sum_{r}(y,r|\omega, x)$

Identification strategy:

Usually mixture model is used to deal with MNAR.

For monotone dropout, MAR is equivalent to ACMV constraints. 

Table here.

### Interior Family Constraints (IFC) ###

1. complete case missing value (CCMV)
2. nearest-neighbour (NN)
3. available case (ACMV) , for monotone dropout, MAR == ACMV
4. non future dependence missing value restrictions
5. identification via extrapolation: $\Sigma$ is common across pattern , then identified

### Mixture Model with discrete time dropout ###

## Pattern Mixture Model with Covariates ##

- linear link: $\beta = \sum \phi_s\beta^{s}$
- nonlinear link: $\beta = \sum_{s} \partial{1}{x} g^{-1}(x\beta^{s}) \phi_{s}(x)$, when $\phi_{s}(x)$ does not depend on x.

## Shared Parameter Model ##

$y |b$ is independent with $r|b$

- $y|x,z \sim N(x\beta+z,\sigma^2)$
- $h_u(t|z) = h_{0}(t)\exp(z\gamma)$

if $\gamma = 0 $ , then MAR, otherwise, MNAR

pros:

1. good at hazard
2. complex data structure
3. latent variable 
4. good at jointly analyzing repeated measure and event time

cons:

1. $y|u$ is not explicit ($p(u|y)$ or p(y|u))
2. $h_{u}$ depend on future observations
3. hard to separate p(ymis|yobs, u), ie, hard to embed MAR
4. rely on $b$ distribution

## Model Selection in Nonignorable Models ##

based on p(y,r|$\omega$) , instead of p(y|$\theta$). While for ignorable data, based on p(y|$\theta$)

- DIC : can be obtained in winbugs
- PPL: posterior predictive checks

# Ch9: Informative Priors and Sensitivity Analysis #

- sensitivity for UN-verifiable missing assumption
- incorporate subjective belief

$p(ymis|yobs, r, \omega_{E})$

## Sensitivity Analysis ##

- fix value constant
- exam inference across range
- assign appropriate prior
- prefer mixture model than selection model

Examples

## Specify Priors ##

- MAR with no uncertainty
- MAR with uncertainty
- MNAR with no uncertainty
- MNAR with uncertainty

Examples
