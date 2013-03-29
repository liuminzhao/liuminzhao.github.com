---
layout: post
title: "fortran notes"
description: ""
tags: [fortran]
---
{% include JB/setup %}

# Version #

1. Fortran77
2. F90/F95

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
	DOUBLE PRECISION: real*8 
	DOUBLE COMPLEX
	CHARACTER
	
	IMPLICIT NONE : add to the beginning of each sub(program)
	
	w = dble(x) * dble(y)

# CONSTANTS #

    1.0
	2.0E6
	.TRUE.
	.FALSE.

# INPUT/OUTPUT #

	READ(*,*) NAME
	WRITE(*,*) 'THE HELLO'
	WRITE(*,*) 'NAME IS ', NAME

# CONDITION #

    if (x .lt. 0) then
	   statements
	elseif (logical) then
	   statements2
	else
	   statements3
	endif

# LOOP #

	Do i=1, 10, 2
		blabla
	end do
	
	Do while
	    statements
	end do
	
use `exit` to exit loop
	
# MATH #	
	
	**: exponential
	
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
	
	.AND.
	.OR.
	.NOT.
	
# FILE #

	OPEN (UNIT=10,FILE='MY_DATA.DAT') # other than 5,6
	READ(10, *) A
	write(10, *) B 
	close(10)

# FUNCTION #

1. function has a type
2. return a value with same name
3. called by name and parameters

    real function r(m,t)
      integer m
      real t

      r = 0.1*t * (m**2 + 14*m + 46)
      if (r .LT. 0) r = 0.0

      return
      end
	  
	  type function name (list-of-variables)
      declarations
      statements
      return
      end

# SUBROUTINE #
	
1. can return more than 1 value	
2. no type 
3. should not be declared in the calling program unit
4. called by `call` 
	
Subroutine has `RETURN`

	subroutine my_sub(a, b)
	
	return
	end
	
`call mysub`

# Reference #

1. <http://www.stanford.edu/class/me200c/tutorial_77/>
