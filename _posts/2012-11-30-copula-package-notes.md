---
layout: post
title: "copula package notes"
description: ""
category: 
tags: [copula; R]
---
{% include JB/setup %}

# Copula Class #

- elliptical (normal and t; ellipCopula)
- Archimedean (Clayton, Gumbel, Frank, Joe, and Ali-Mikhail-Haq; ; archmCopula and acopula)
- extreme value (Gumbel, Husler-Reiss, Galambos, Tawn, and t-EV; evCopula)
- families (Plackett and Farlie-Gumbel-Morgenstern).

# Density, CDF, random variable generation #

- `dCopula`, `pCopula`, `rCopula`
- bivariate dependence measure (`rho`, `tau`, etc)
- perspective and contour plots

	    persp(norm.cop, dCopula)
		contour(norm.cop, pCopula)
		scatterplot3d(rCopula(1000, norm.cop))

# Fitting Model #

- Functions (and methods) for fitting copula models including variance estimates (fitCopula).

	example(fitCopula)## fitting Copulas
    example(fitMvdc)  ## fitting multivariate distributions via Copulas

	fitCopula
	loglikCopula
	

# EllipCopula #
	
	ellipCopula (family, param, dim = 2, dispstr = "ex", df = 4, ...)
    normalCopula(param, dim = 2, dispstr = "ex")
	tCopula (param, dim = 2, dispstr = "ex", df = 4, df.fixed = FALSE)

Implemented structures are "ex" for ex- changeable, "ar1" for AR(1),
"toep" for Toeplitz, and "un" for unstructured.  

	 norm.cop <- normalCopula(c(0.5, 0.6, 0.7), dim = 3, dispstr = "un")
    t.cop <- tCopula(c(0.5, 0.3), dim = 3, dispstr = "toep",
                     df = 2, df.fixed = TRUE)
    ## from the wrapper
    norm.cop <- ellipCopula("normal", param = c(0.5, 0.6, 0.7),
                            dim = 3, dispstr = "un")
    if(require("scatterplot3d")) {
      ## 3d scatter plot of 1000 random observations
      scatterplot3d(rCopula(1000, norm.cop))
      scatterplot3d(rCopula(1000, t.cop))
	  }

# mvdc #

	mvdc(copula, margins, paramMargins, marginsIdentical = FALSE,
         check = TRUE, fixupNames = TRUE)
    dMvdc(x, mvdc, log=FALSE)
    pMvdc(x, mvdc)
    rMvdc(n, mvdc)


# Code #

[file](~/Documents/copula/test.R)
