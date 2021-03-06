---
layout: page
title: "Q57971: Unresolved Externals from GRAPHICS.LIB"
permalink: /kb/057/Q57971/
---

## Q57971: Unresolved Externals from GRAPHICS.LIB

{% raw %}

	Article: Q57971
	Product(s): See article
	Version(s): 5.10
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | s_quickc s_quickasm | mspl13_c
	Last Modified: 26-JAN-1990
	
	When linking a program with a version of GRAPHICS.LIB newer than the
	one supplied with your compiler, the following unresolved externals
	will occur:
	
	   LINK : error L2029: Unresolved externals:
	
	   __aDBdoswp in file(s):
	    d:\lib\GRAPHICS.LIB(..\gr\qcswap.asm)
	   ___aDBswpchk in file(s):
	    d:\lib\GRAPHICS.LIB(..\gr\qcswap.asm)
	   ___aDBswpflg in file(s):
	    d:\lib\GRAPHICS.LIB(..\gr\qcswap.asm)
	
	   There were 3 errors detected
	
	Code Example
	------------
	
	#include <stdio.h>
	#include <graph.h>
	
	void main(void)
	{
	    _clearscreen ( _GCLEARSCREEN );
	    _settextcolor ( 1L );
	    _outtext ("Hello");
	    getch();
	}
	
	Following are the steps to re-create the unresolved externals:
	
	1. Compile the program using Microsoft C 5.10 compiler and link the
	   object file with GRAPHICS.LIB from either FORTRAN 5.00, QuickC
	   2.00, or QuickC 2.01.
	
	2. Compile the program using Microsoft QuickC 2.00 or 2.01 and link
	   the object file with GRAPHICS.LIB from FORTRAN 5.00.
	
	To determine which GRAPHICS.LIB came with which package, check the
	size of the GRAPHICS.LIB file (shown below):
	
	   C 5.10                       - 59357 bytes   3-07-88   5:10a
	
	   QuickC 2.00                  - 75337 bytes  12-13-88  10:19a
	
	   QuickC w/QuickAssembler 2.01 - 75871 bytes   3-08-89  11:17a
	
	   FORTRAN 5.00                 - 76467 bytes   3-24-89   8:56p
	
	It is recommended that you use the version of GRAPHICS.LIB that comes
	with the compiler to avoid any problems.

{% endraw %}
