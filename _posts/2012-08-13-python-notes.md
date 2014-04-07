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

# Reference #

1. <http://maxburstein.com/blog/python-shortcuts-for-the-python-beginner/>

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

## Special character ##

`\` is `\\`. Check out using `print string`. Also  define string including `\` using raw definition:

	a = r'\documentclass{article}'

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

## write

	file = open(yourfile, 'a')
	file.write(string)
	file.close()

# sort #

	list.sort()
	mydict = {'a': 1, 'b':2, 'c':3}
	sorted(.., key = lambda key: mydict[key])
	number = ''.join(sorted(hand[0:14:3], key = carddict.get))

	sorted[(a, b)]

sort by second column <http://xahlee.info/perl-python/sort_list.html> :

    list.sort(lambda x, y: cmp(x[1], y[1]))
	list.sort(key = lambda x:x[1], reverse = True)

# Area #

Triangle area:

    def area2(a, b, c):
    ax, ay = a
    bx, by = b
    cx, cy = c
    return (bx - ax)*(cy - ay) - (cx - ax)*(by - ay)


# list #

	range(10)
	range(3, 10, 2)
	list()
	x.append(xn)
	x[-1] : last one
	x[-2] : second to last

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

* divide: `//`
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
* elpy

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

item / value:

	dict.items()
	for key, value in dict.items():


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
	x = range(5)
	random.shuffle(x)


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

# Regular Expression :Regex #

    import re
	p = re.compile('ab*')
	m = p.match()
	m = p.search()
	findall()
	finditer()

Methods:

    m.group(): return string
	m.start():
	end()
	span():
	for match in p.finditer():
	    print match.start()

Modifying Strings:

    split()
	sub()
	re.sub(' +', ' ', str)


# Coursera course Notes (Interactive Programming) #

Event driven program:

start - initial -wait(event, handler)

1. Input:
- button
- text box
2. keyboard:
- key down
- key up
3. mouse:
- click
- drag
4. timer

Structure:

1. globals
2. help functions
3. classes
4. define event handlers
5. create a frame
6. register event handlers
7. start frame and timers

## SimpleGui ##

    def div():
    """ divide store by operand"""
    global store
    store = store / operand
    output()

    def enter(t):
       """ enter a new operand"""
       global operand
       operand = int(t)
       output()
    f = simplegui.create_frame("Calculator",300,300)
	f.add_button("Print", output, 100)
	f.add_input("Enter", enter, 100)

### Canvas (draw handler) ###

	# define draw handler
	def draw(canvas):
    canvas.draw_text("Hello!",[100, 100], 24, "White")
    canvas.draw_circle([100, 100], 2, 2, "Red")

	# create frame
	frame = simplegui.create_frame("Text drawing", 300, 200)

	# register draw handler
	frame.set\_draw\_handler(draw)

### Timer ###

	timer1 = simplegui.create_timer(itnerval, handler)
	timer1.start()

## Keyboard ##

    def keydown(key):
	    current = chr(key)
		if key == simplegui.KEY_MAP["left"] # "right", "down", "up"
	f.set\_keydown\_handler(keydown)
	f.set\_keyup\_handler(keyup)

### Mouse ###

handler:

	def mouseclick\_handler(position):  # position: (x, y)

register:

	frame.set\_mouseclick\_handler(click)

### Image ###

	im = simplegui.load_image(URL)
	canvas.draw_image(im, center, size)

### Sound ###

	music.play()
	music.pause()
	music.rewind()
	music = simplegui.load_sound(url)
	music.set_volume(num)

## Class ##

	class Character: # capitalize
		def __init__(self, name, init_heal):
			self.name = name
			self.health = init_heal
			self.inventory = []  # no need to return anything
		def __str__(self):
			s  = "Name: " + self.name
			s += " Health: " + str(self.health)
			return s
		def grab(self, item):
			self.inventory.append(item)
		def get_health(self):
			return self.health

use:

	me = Character("Bob", 20)
	print str(me)
	me.grab("pencil")
	print str(me)

# os #

`os` module can use shell or other system command. `subprocess` is the new updated and more powerful tool.
However, `os` is much easier for one time use and for newbie like me.

## change working directory ##

	owd = os.getcwd()
	os.chdir(testDir)
	os.chdir(owd)

# Command use #

	import os
	if __name__ == "__main__":
		...

	python yourfile.py

or use:

	#!/usr/bin/python
	#!/usr/bin/env python

`sys.argv` is the list of command line arguments. The first element is the name of the program.

## Sys ##

Print out error and exit

	sys.exit('error message!')


# Matplot

<http://nbviewer.ipython.org/github/jrjohansson/scientific-python-lectures/blob/master/Lecture-4-Matplotlib.ipynb>

	from pylab import *

or

	import matplotlib.pyplot as plt

## Matlab-like API Example:

	x = linspace(0, 5, 10)
	y = x ** 2
	figure()
	plot(x, y, 'r')
	xlabel('x')
	ylabel('y')
	title('title')
	show()

## Subplot:

	subplot(1, 2, 1)
	plot(x, y, 'r--') # red , dashed
	subplot(1, 2, 2)
	plot(y, x, 'g*-');

layout managers in matplotlib

	fig, axes = plt.subplots()

	axes.plot(x, y, 'r')
	axes.set_xlabel('x')
	axes.set_ylabel('y')
	axes.set_title('title');

subplot:

	fig, axes = plt.subplots(nrows=1, ncols=2)

	for ax in axes:
		ax.plot(x, y, 'r')
		ax.set_xlabel('x')
		ax.set_ylabel('y')
		ax.set_title('title')

	fig.tight_layout()

## OO API

	fig = plt.figure()
	axes = fig.add_axes([0, 0, 1, 1]) # left, bottom, width, height (range 0 to 1)
	axes.plot(x, y, 'r')
	axes.set_xlabel('x')
	axes.set_ylabel('y')
	axes.set_title('title')

Picture in picture:

	fig = plt.figure()

	axes1 = fig.add_axes([0.1, 0.1, 0.8, 0.8]) # main axes
	axes2 = fig.add_axes([0.2, 0.5, 0.4, 0.3]) # inset axes

	# main figure
	axes1.plot(x, y, 'r')
	axes1.set_xlabel('x')
	axes1.set_ylabel('y')
	axes1.set_title('title')

	# insert
	axes2.plot(y, x, 'g')
	axes2.set_xlabel('y')
	axes2.set_ylabel('x')
	axes2.set_title('insert title');

## Figure size and DPI

an 800x400 pixel, 100 dots-per-inch figure,

	fig = plt.figure(figsize=(8,4), dpi=100)


## Save

	fig.savefig("filename.png", dpi=200)

## Legends

	ax.legend(["curve1", "curve2"])

Better way:

	ax.plot(x, x**2, label = "curve1")
	ax.plot(x, x**2, label = "curve2")
	ax.legend()

Loc

	ax.legend(loc = 0) # auto
	ax.legend(loc = 1) # upper right, 2 = upper left , 3 = lower left , 4 = lower right

## Latex support

	label=r"$y = \alpha^2$"
	ax.set_ylabel(r'$y$', fontsize=18)

## Font

	matplotlib.rcParams.update({'font.size': 18, 'font.family': 'serif'})

## Color, lw, lt

	# MATLAB style line color and style
	ax.plot(x, x**2, 'b.-') # blue line with dots
	ax.plot(x, x**3, 'g--') # green dashed line
	ax.plot(x, x+1, color="red", alpha=0.5) # half-transparant red
	ax.plot(x, x+2, color="#1155dd")        # RGB hex code for a bluish color
	ax.plot(x, x+3, color="#15cc55")        # RGB hex code for a greenish color

lw, linestyle

	# possible linestype options ‘-‘, ‘–’, ‘-.’, ‘:’, ‘steps’
	ax.plot(x, x+5, color="red", lw=2, linestyle='-')
	ax.plot(x, x+6, color="red", lw=2, ls='-.')
	ax.plot(x, x+7, color="red", lw=2, ls=':')

Marker:

	# possible marker symbols: marker = '+', 'o', '*', 's', ',', '.', '1', '2', '3', '4', ...
	ax.plot(x, x+ 9, color="green", lw=2, ls='*', marker='+')
	ax.plot(x, x+10, color="green", lw=2, ls='*', marker='o')
	ax.plot(x, x+11, color="green", lw=2, ls='*', marker='s')
	ax.plot(x, x+12, color="green", lw=2, ls='*', marker='1')

	# marker size and color
	ax.plot(x, x+13, color="purple", lw=1, ls='-', marker='o', markersize=2)
	ax.plot(x, x+14, color="purple", lw=1, ls='-', marker='o', markersize=4)
	ax.plot(x, x+15, color="purple", lw=1, ls='-', marker='o', markersize=8, markerfacecolor="red")
	ax.plot(x, x+16, color="purple", lw=1, ls='-', marker='s', markersize=8,

## Plot range

	axe.set_ylim([0, 50])

or

	axis('tight')

Log scale:

	axe.set_yscale("log")

## Grid

	axe.grid(True)
	axes[1].grid(color='b', alpha=0.5, linestyle='dashed', linewidth=0.5)

## Other method

### scatter

	axes[0].scatter(xx, xx + 0.25*randn(len(xx)))

### Step

	axes[1].step(n, n**2, lw=2)

### bar

	axes[2].bar(n, n**2, align="center", width=0.5, alpha=0.5)

### fill

	axes[3].fill_between(x, x**2, x**3, color="green", alpha=0.5);

## Gallery

1. <http://nbviewer.ipython.org/github/cs109/content/blob/master/lec_03_statistical_graphs_mpl_default.ipynb>
2. <http://nbviewer.ipython.org/github/cs109/content/blob/master/lec_03_statistical_graphs.ipynb>

# Email

<http://rosettacode.org/wiki/Send_an_email#Python>

	import smtplib

	def sendemail(from_addr, to_addr_list, cc_addr_list,
              subject, message,
              login, password,
              smtpserver='smtp.gmail.com:587'):
    header  = 'From: %s\n' % from_addr
    header += 'To: %s\n' % ','.join(to_addr_list)
    header += 'Cc: %s\n' % ','.join(cc_addr_list)
    header += 'Subject: %s\n\n' % subject
    message = header + message

    server = smtplib.SMTP(smtpserver)
    server.starttls()
    server.login(login,password)
    problems = server.sendmail(from_addr, to_addr_list, message)
    server.quit()
    return problems


Example:

	sendemail(from_addr    = 'python@RC.net',
          to_addr_list = ['RC@gmail.com'],
          cc_addr_list = ['RC@xx.co.uk'],
          subject      = 'Howdy',
          message      = 'Howdy from a python function',
          login        = 'pythonuser',
          password     = 'XXXXX')

# Unicode

	print a.encode('utf-8')
