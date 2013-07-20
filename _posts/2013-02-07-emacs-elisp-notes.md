---
layout: post
title: "emacs elisp notes"
description: ""
category:
tags: [emacs, elisp]
---
{% include JB/setup %}

# Reference #

- <http://ergoemacs.org/emacs/elisp_basics.html>
- <http://ergoemacs.org/emacs/elisp.html>



# Printing #

	(message "hi")
	(message "%d" 16)
	(message "%S" (list 3 4 5)) ; for any lisp exp

# Arithmetic #

	(+ 4 5)
	(% 7 5)
	(expt 2 3)
	(< 3 4)
	(/= 3 4 )  ; not equal
	(string-equal "this" "this")
	(equal 3 5); compare the datatype too

# True False #

In elisp, the symbol nil is false, anything else is considered true. So, 0 is true, and empty string "" is also true. Also, nil is equivalent to the empty list (), so () is also false.

# Variables #

	(setq x 1 y 3 z 5)

# IF Then Else #

	(if (< 3 2) True Statement False Statement) ; False can be multiple statements

Block expression:

	(progn (message "a") (message "b"))

	(if something
	(progn ; true
	…
	)
	(progn ; else
	…
	)
	)

# Iteration #

	(while (< x 4)
		(print (format "yay %d" x))
		(setq x (1 + x)))

# Function #

	(defun myFunction()
		"test"
		(message "Yes")) ; last is returned.

	(interactive) ; can be called by M - x

# Eval #

	(eval command)

# Vectors #

	(setq v (vector 3 4 5))
	(setq v [3 4 5])
	(length (vector 3 4 5))

# list #

	(list 1 2 3 )
	'(a b)
	(car myList) ; first
	(nth n mylist)
	(car (last myList)) ; last
	(cdr myList); 2nd to last
	(nthcdr n myList);nth to last
	(butlast myList n); without the last n elements
	(length mList)
	(cons x myList) ; add x to front
	(append list1 list2) ; join 2
	(pop mylist)

# Typical Command Template #

	(defun myCommand ()
  "One sentence summary of what this command do.

	More details here. Be sure to mention the return value if relevant.
	Lines here should not be longer than 70 chars,
	and don't indent them."
	(interactive)
	(let (localVar1 localVar2 …)
	(setq localVar1 …)
	(setq localVar2 …)
	…
	;; do something …
		)
	)

# Tips #

	(member 3 '(1 2 3))
	(string-to-number "3")
	(number-to-string 3)
