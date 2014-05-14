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
- <http://bzg.fr/learn-emacs-lisp-in-15-minutes.html>


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

	(defun greeting (from-name)
	(let ((your-name (read-from-minibuffer "Enter your name: ")))
    (insert (format "Hello!\n\nI am %s and you are %s."
    from-name ; the argument of the function
    your-name ; the let-bound var, entered at prompt
    ))))

	(defun hello () (insert "Hello, I am " my-name))
	(defun hello (name) (insert "Hello " name))

Evaluate:

	(hello)
	(hello "you")
	(switch-to-buffer-other-window "\*test\*")

# Eval #

	(eval command)
	C-j
	C-x C-e : displays in minibuffer


# Vectors #

	(setq v (vector 3 4 5))
	(setq v [3 4 5])
	(length (vector 3 4 5))
	(setq my-name "Bastien")

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

	(let ((local-name "you"))
	(switch-to-buffer-other-window "*test*")
	(erase-buffer)
	(hello local-name)
	(other-window 1))


# Tips #

	(member 3 '(1 2 3))
	(string-to-number "3")
	(number-to-string 3)

# Command #

`insert` : where the cursor is

	(insert "Hello!")
	(insert "Hello" " world!")
	(insert "Hello, I am " my-name)

**combine** with `progn`

	(progn
	(switch-to-buffer-other-window "*test*")
	(hello "you"))

	(erase-buffer) : erase
	(other-window 1) :go back to the other window

`format`:

	(format "Hello %s!\n" "visitor")

`let` bind a value to a local variable with `let':

	(defun greeting (name)
	(let ((your-name "Bastien"))
    (insert (format "Hello %s!\n\nI am %s."
    name       ; the argument of the function
    your-name  ; the let-bound variable "Bastien"
    ))))

# application

## round all number in region

<http://stackoverflow.com/questions/23636226/how-to-round-all-the-numbers-in-a-region>

	(defun my-round-nb (start end)
	"round the nb of the region."
	(interactive "r")
	(save-restriction
    (narrow-to-region start end)
    (goto-char 1)
    (let ((case-fold-search nil))
    (while (search-forward-regexp "\\([0-9]+\\.[0-9]+\\)" nil t)
	(replace-match (format "%0.1f" (string-to-number (match-string 1)))
	)))))

or

	C-M-%[0-9]+\.[0-9]+RET\,(format "%0.2f" \#&)RET

The `\,(...)` in the replacement text means to interpolate the result of calling the parenthesized Lisp expression, and `\#&` means "whatever the entire pattern matched, converted to a number."
