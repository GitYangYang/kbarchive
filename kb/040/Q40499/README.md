---
layout: page
title: "Q40499: Internal Compiler Error: regMD.c 1.117 Line 292"
permalink: /kb/040/Q40499/
---

## Q40499: Internal Compiler Error: regMD.c 1.117 Line 292

{% raw %}

	Article: Q40499
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist5.10 | mspl13_c
	Last Modified: 14-JUL-1989
	
	The following error is produced when the code sample below is compiled
	in either the large- or compact-memory models (/AL and /AC):
	
	       fatal error C1001: Internal Compiler Error
	        (compiler file '@(#)regMD.c:1.117', line 292)
	        Contact Microsoft Technical Support
	
	The memory models small, medium, and huge do not generate this error.
	This error is produced with optimizations disabled as well as with the
	default optimizations. The error occurs on the following line:
	
	   temp_sub[x + 1] = Themain.sub[x];
	
	The workaround to this problem is to declare a temporary structure to
	serve as an intermediate storage place for this assignment as follows:
	
	   temp = Themain.sub[x] ;
	   temp_sub[x+1] = temp ;
	
	Microsoft has confirmed this to be a problem with Version 5.10 of the
	C compiler. We are researching this problem and will post new
	information as it becomes available.
	
	The code below produces the offending internal compiler error. The
	workaround has been noted and commented out.
	
	The following is a code example:
	
	struct   main_def
	 {
	   struct   sub_def
	    {
	      int      max_width;
	      long     start_byte, end_byte;
	    } *sub;
	
	 } Themain;
	
	static int test (int x)
	{
	   struct sub_def *temp_sub, temp ;
	
	   /*                           To workaround the error, replace
	   temp = Themain.sub[x] ;      the assignment below with these two.
	   temp_sub[x+1] = temp ;
	   */
	
	   temp_sub[x + 1] = Themain.sub[x];  /* Error occurs on this line. */
	}

{% endraw %}
