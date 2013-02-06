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
	
three data types 

* integers
* floats
* booleans : `True` , `False`

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

# Conditions #

	if 8<9 :
		print 
	elif 8>9:
		print
	else:
		print

	print "Hello" if True else "World"

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



# loop #

	for x in range(10):
		tmp=stat
		break

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
		
	f.close()

# sort #

	list.sort()
	mydict = {'a': 1, 'b':2, 'c':3}
	sorted(.., key = lambda key: mydict[key])
	number = ''.join(sorted(hand[0:14:3], key = carddict.get))




# list #

	range(10)
	range(3, 10, 2)
	list()
	x.append(xn)
	
check exist in a list 
	
	if x in prime 
	
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

emacs for python <https://github.com/gabrielelanaro/emacs-for-python/>

* install ipython
* install nose
* install readline

# Debug #

- `c` : continue to breakpoint
- `n` : next
- `p` : watch variable 
- `w` and `u`, `d`

# Tips #

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
	
# Reference #

1. <http://maxburstein.com/blog/python-shortcuts-for-the-python-beginner/>
