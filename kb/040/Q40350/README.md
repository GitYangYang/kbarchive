---
layout: page
title: "Q40350: _getimage Buffer May Be Huge (Larger than 64K)"
permalink: /kb/040/Q40350/
---

## Q40350: _getimage Buffer May Be Huge (Larger than 64K)

{% raw %}

	Article: Q40350
	Product(s): See article
	Version(s): 5.00 5.10
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | S_QuickC | mspl13_c
	Last Modified: 16-JAN-1989
	
	The graphics functions _getimage and _putimage may be used to store
	and display graphic images that require a buffer size larger than 64K.
	Even though these functions specify that the storage buffer is a far
	pointer, _getimage and _putimage internally treat the buffer as huge
	and do 32-bit address arithmetic.
	
	The following program demonstrates using the image functions on a huge
	image.
	
	/********************************************************************
	 * Example program to demonstrate using the functions _getimage and *
	 * _putimage on a huge image.                                       *
	 ********************************************************************/
	
	#include <stddef.h>
	#include <malloc.h>
	#include <process.h>
	#include <graph.h>
	
	void main (void)
	 { long size;
	   char far *image;
	
	   /* Put the display in a VGA mode and allocate a huge buffer. */
	   if (_setvideomode(_VRES16COLOR)==0)
	       { _outtext ("Video mode not supported!\n");
	         exit (0);
	       }
	
	   /* In _VRES16COLOR, size is 153604. */
	   size = _imagesize(0,0,639,479);
	
	   if ( (image=halloc(size,1)) == NULL)
	       { _outtext ("Not enough memory for buffer!\n");
	         exit (0);
	       }
	
	   /* Draw a couple shapes and capture the screen. */
	   _ellipse (_GBORDER,0,0,639,479);
	   _rectangle (_GBORDER,0,0,639,479);
	   _getimage (0,0,639,479,image);
	
	   /* Clear the screen and redraw the image. */
	   _clearscreen (_GCLEARSCREEN);
	   _putimage (0,0,image,_GOR);
	
	   hfree (image);
	 }

{% endraw %}
