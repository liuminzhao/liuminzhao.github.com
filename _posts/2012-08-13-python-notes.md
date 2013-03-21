---
layout: post
title: "python notes"
description: ""
category: 
tags: [python]
---
{% include JB/setup %}

Python Notes
==========

# variable #

	my_variable=10
	
Global:
	
	_a = 1
	
three data types 

* integers
* floats
* booleans : `True` , `False`

	type(a)

# print #

	print my_int
	print("%.2f" % total)
	print "MOnty" + " " + "fsd"
	print "fdsf \%\s , \%\s" % (str1, str2)
	
# Date and Time #	

	from datetime import datetime
	now = datetime.now()
	now.year, now.month, now.day/hour/minute/second
	
	today = datetime.date.today()
	today - datetime.timedelta(days=today.weekday())

# Time #

	import time
	time.time()

# Conditions #

	if 8<9 :
		print 
	elif 8>9:
		print
	else:
		print

	print "Hello" if True else "World"

	x = 3 if (y == 1) else 2
	x = ((y == 1) ? 3 : 2)

# function #

	def fun(bill, param2):
		bill*=1.08
		print bill
		return bill

# import modules #

	import math
	math.sqrt(25)
	from module import function
	from module import *

	import math
	everything = dir(math)
	print everything

# String #

	book="book"
	\'
	"MONTY"[4]
	'='*10 

	name= [one.strip('"') for one in f.readline().split(",")]

	ord(char) 

Reverse:

	string[::-1] 
	string[begin:end:step]

base 10 to binary 

	x = bin(30)[2:]
	int(x, 2)

## Join List to String ##

	teams = ["Packers", "49ers", "Ravens", "Patriots"]
	print ", ".join(teams)
	>>> 'Packers, 49ers, Ravens, Patriots'

# Method #

	len()
	parrot.lower()
	parrot.upper()
	str()

because len() and str() are generic function, lower and upper are only for 
strings

# Iteration/Permutation/combination #

	import itertools
	x = list(itertools.permutations([1,2,3]))
	list(itertools.product(*index))


# loop #

	for x in range(10):
		tmp=stat
		break
	else: 
		bla

	while true:
		statement
		break
		
	if true : 
		statement
		

# change class #
	
	int()
	float()

# file #

	f=open('e11.txt', 'r')
	f.seek() 
	f.readline()
	f.read()
	for line in f:
		print line
	else: 
		bla
	f.close()

Use `with`, 

    with open('foo') as myfile:
	    print myfile.closed


# sort #

	list.sort()
	mydict = {'a': 1, 'b':2, 'c':3}
	sorted(.., key = lambda key: mydict[key])
	number = ''.join(sorted(hand[0:14:3], key = carddict.get))

	sorted[(a, b)]


# list #

	range(10)
	range(3, 10, 2)
	list()
	x.append(xn)
	
check exist in a list 
	
	if x in prime 
	
	
# Tuple #

protected. 

	a = ("a", 'b')

# unique #
	
	list(set(x))

# Comment #

	# 
	"""fsafdaf"""
	
# Math #
	
* expo : `**`
* mod `%`
* equal `==`
* and `and` `or`, `not`
* `max`, `min`, `abs`, `type`
* math import
** `ceil`
** `fabs(x) = abs(x)`
** `factorial(x)`
** `log`
** `pi`, `e`
** xor: `^`
** chr(107) and ord('k')


# build in function #

	sum

# List/Matrix #

	x = [[foo for i in range(10)] for j in range(10)] 
	prime= [x for x in range(2,200) if not [t for t in range(2,int(math.sqrt(x))+1) if not x%t]]
	factors = [ x for x in range(2, n) if not n%x]

# digit sum #

	sum([int(one) for one in str(number)])

# Emacs #

* rope
* ropemacs
* ipython
* pymacs

	    C-c C-c
		C-c | # region
		C-M-x # eval function

emacs for python <https://github.com/gabrielelanaro/emacs-for-python/>

* install ipython
* install nose
* install readline

Jedi <https://github.com/tkf/emacs-jedi>:

	M-x list-package
	

# Debug #

- `c` : continue to breakpoint
- `n` : next
- `p` : watch variable 
- `w` and `u`, `d`

# Plot #
 
    import pylab
	x = numpy.linspace(-1, 1, 50)
	pylab.plot(x, f(x), result, pow3(result), 'ro')
	pylab.grid(b = 1)
	pylab.show()

# Use R function in Python #

    easy_install rpy2
	import rpy2.robjects as robjects
	r = robjects.r
	dnorm = r.dnorm
	
calling R function returns a R object, need to turn it to `numpy.array`

Also need to create R vectors:

    res = robjects.StrVector(['abc', 'def'])
    res = robjects.IntVector([1, 2, 3])
	res = robjects.FloatVector([1.1, 2.2, 3.3])
	
then can use

    dnorm(res)
	
# Tips #

Do not use `*` to import all. Use `import numpy as np` . 

## Change Var ##

	x, y = y, x

## Compare ##

	if 3 > x > 1:

## Simultaneous Loop ##

	nfc = ["Packers", "49ers"]
	afc = ["Ravens", "Patriots"]
	for teama, teamb in zip(nfc, afc):
		print teama + " vs. " + teamb
	>>>; Packers vs. Ravens
	>>>; 49ers vs. Patriots

## Enumerate ##

	teams = ["Packers", "49ers", "Ravens", "Patriots"]
	for index, team in enumerate(teams):
		print index, team
	>>> 0 Packers
	>>> 1 49ers
	>>> 2 Ravens
	>>> 3 Patriots

## Dict ##

	teams = ["Packers", "49ers", "Ravens", "Patriots"]
	print {key: value for value, key in enumerate(teams)}
	>>> {'49ers': 1, 'Ravens': 2, 'Patriots': 3, 'Packers': 0}
	
	teams['49ers']
	
keys:

	dict.keys()
	
## Initial ##

	item = [0]*3  # [0, 0, 0]
	
## Subset in List ##

	x[:3] # first three
	x[3:] # last three
	x[::2] # odds item
	x[1::2] # even item
	
## Counter ##	
	
	from collections import Counter
	print Counter("hello")
	>>> Counter({'l': 2, 'h': 1, 'e': 1, 'o': 1})
	
## Itertools ##
	
	from itertools import combinations
	teams = ["Packers", "49ers", "Ravens", "Patriots"]
	for game in combinations(teams, 2):
	print game
	>>> ('Packers', '49ers')
	>>> ('Packers', 'Ravens')
	>>> ('Packers', 'Patriots')
	>>> ('49ers', 'Ravens')
	>>> ('49ers', 'Patriots')
	>>> ('Ravens', 'Patriots')
	
## Other ##
	
	"fizz"[x%3*4::]

# Python for Scientific Computation #

Book <http://hyry.dip.jp:8000/pydoc/index.html>

## Software ##

- numpy
- scipy
- sympy

## Numpy ##

	import numpy as np
	
ndarray is much faster than array or list in python.

Create:

	c = np.array([[1, 2, 3, 4],[4, 5, 6, 7], [7, 8, 9, 10]])
	
Size

	c.shape
	
Reshape : do not change order,  just change shape

	c.shape = 4, 3
	c.shape = 2, -1 # auto change col dim
	d = c.reshape((2, 2)) 
	
d and c share the same memory. 
	
`arange`:

	>>> np.arange(0,1,0.1)
	array([ 0. ,  0.1,  0.2,  0.3,  0.4,  0.5,  0.6,  0.7,  0.8,  0.9])

`linspace`:

	np.linspace(0, 1, 12)
	
`logspace` for dengbi:

	np.logspace(0, 2, 20)

Multi-level array:

	a[4:, 4:]

Append:

    np.append([2], primes)

`struct`

	import numpy as np
	persontype = np.dtype({
    'names':['name', 'age', 'weight'],
    'formats':['S32','i', 'f']})
	a = np.array([("Zhang",32,75.5),("Wang",24,65.2)],
    dtype=persontype)

### ufunc ###

	np.sin(x)
	np.sin(x, x) 
	np.add
	subtract
	multiply
	divide
	truedivide
	floor divide
	negative
	power
	remainder/mod
	np.cumsum
	
	add.reduce
	add.accumulate(, axis = )
	
	np.multiply.outer([1,2,3,4,5],[2,3,4])
	array([[ 2,  3,  4],
       [ 4,  6,  8],
       [ 6,  9, 12],
       [ 8, 12, 16],
       [10, 15, 20]])

### Matirx ###

	a = np.matrix
	a**-1
	np.dot(a, b)
	np.alltrue
	np.inner
	np.outer
	np.random.rand(10, 10)
	np.linalg.solve(a, b)

## Scipy ##

### Least Square and Plot###

	from scipy.optimize import leastsq
	import numpy as np
	import math
	def res(p, y, x):
    theta0, theta1 = p
    return y - theta0*math.e**(-theta1*x)
	x = np.arange(1, 8)
	y = [0.1024,0.08471,0.07525,0.06275,0.06131,0.06047,0.05736]
	from scipy.optimize import leastsq
	p0 = [0.1, 0]
	plsq = leastsq(res, p0, args = (y, x))
	print plsq[0]

	import matplotlib.pyplot as plt
	def pevel(x, p):
    return p[0]*math.e**(-p[1]*x)
	plt.plot(x, pevel(x, plsq[0]), x, y)
	plt.legend(['ft', 'true'])
	plt.show()


### fmin ###

### fsolve for finding root or zero of a function###

    from scipy.optimize import fsolve
	pow3 = lambda x : x**3
	result = fsolve(pow3, 10) # starting point

### Spline ###

	from scipy import interpolate
	x = np.linspace(0, 2*np.pi+np.pi/4, 10)
	y = np.sin(x)
	x_new = np.linspace(0, 2*np.pi+np.pi/4, 100)
	f_linear = interpolate.interp1d(x, y)
	tck = interpolate.splrep(x, y)
	y_bspline = interpolate.splev(x_new, tck)

	pl.plot(x, y, "o",  label=u"原始数据")
	pl.plot(x_new, f_linear(x_new), label=u"线性插值")
	pl.plot(x_new, y_bspline, label=u"B-spline插值")
	pl.legend()
	pl.show()

### Integral ###

	np.trapz
	from scipy import integrate
	integrate.quad


	import PIL
	im = Image.open("lena.png")
	im.show()
	im.size
	im.getpixel()

# Pickel #

	import pickle
	pickle.load(f)

# Lambda function #

	#define function in variable then call
	g = lambda x: x*2
	g(3)
	skip variable, just call
	(lambda x: x*2)(3)

# Random #

	import random
	random.randint(a, b)
	import numpy.random
	npr.random_integers # much faster than random module

# Fast Way to Generator Primes #

From stackoverflow: <http://stackoverflow.com/questions/2068372/fastest-way-to-list-all-primes-below-n-in-python>

	def primesfrom2to(n):
    """ Input n>=6, Returns a array of primes, 2 <= p < n """
    sieve = np.ones(n/3 + (n%6==2), dtype=np.bool)
    for i in xrange(1,int(n**0.5)/3+1):
        if sieve[i]:
            k=3*i+1|1
            sieve[       k*k/3     ::2*k] = False
            sieve[k*(k-2*(i&1)+4)/3::2*k] = False
    return np.r_[2,3,((3*np.nonzero(sieve)[0][1:]+1)|1)]



# Reference #

1. <http://maxburstein.com/blog/python-shortcuts-for-the-python-beginner/>
