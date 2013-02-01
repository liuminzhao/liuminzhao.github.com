---
layout: post
title: "fortran notes"
description: ""
tags: [fortran]
---
{% include JB/setup %}

# Syntax #

1. not case sensitive
2. 6 spaces; max 72 width
3. `c` for comment
4. `&` or `*` at 6th space for continue
5. program and subroutine 

	    program my_prog
		
		end
		
		subroutine my_sub
		
		end

# Declare #

	REAL
	INTEGER
	COMPLEX
	DOUBLE PRECISION
	DOUBLE COMPLEX
	CHARACTER
	
	IMPLICIT NONE

# INPUT/OUTPUT #

	READ(*,*) NAME
	WRITE(*,*) 'THE HELLO'
	WRITE(*,*) 'NAME IS ', NAME
	
# LOOP #

	Do i=1, 10
		blabla
	end do
	
	Do while
	
	end do
	
# COMPARE #

	.GT.
	.GE.
	.EQ.
	.LE.
	.LT.
	.NE.
	
	If (A .LT. 0.0) A = (-1)*A
	
	If () THEN
		JJJ
	ELSE
	    JJJ
	END IF
	
# FILE #

	OPEN (UNIT=10,FILE='MY_DATA.DAT') # other than 5,6
	READ(10, *) A
	write(10, *) B 
	close(10)
	
# SUBROUTINE #
	
Subroutine has `RETURN`

	subroutine my_sub(a, b)
	
	return
	end
	
`call mysub`
