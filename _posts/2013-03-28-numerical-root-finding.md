---
layout: post
title: "numerical root finding"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Numerical Root Finding Methods
==========

- <http://www.efunda.com/math/num_rootfinding/num_rootfinding.cfm>
- <http://www.fing.edu.uy/if/cursos/fiscomp/extras/numrec/book/f9.pdf>

# Bisection #

    pick tol
	x = (a + b)/2
	if (abs(f(x)) < tol) : stop
	else: 
	    if (f(x)f(b) < 0) a = x, b = b
		else a = a, b = x

1. slowest
2. can only find one
3. contains singular, then bisection method converges to the singularity

# Secant #

extrapolation or interpolation lines through the two most recently evaluated points,
whether or not they bracket the function.

    x_k+1 = x_k - (xk - xk_1)/(f(xk) - f(xk_-1)) * f(xk)

# False Position #

 false position method retains the most recent estimate and the next recent one which has an opposite sign in the function value. 
  
  
# Newton-Raphson #

    x(t+1) = x(t) - f(x(t))/f'(x(t)) 

requires the derivative

A numerical way:

    f'(x) = (f(x + dx) - f(x))/dx
