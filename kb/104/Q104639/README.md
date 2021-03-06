---
layout: page
title: "Q104639: INFO: Dynamic Memory Allocation for Two-Dimensional Arrays"
permalink: /kb/104/Q104639/
---

## Q104639: INFO: Dynamic Memory Allocation for Two-Dimensional Arrays

{% raw %}

	Article: Q104639
	Product(s): Microsoft C Compiler
	Version(s): MS-DOS:6.0ax,7.0;OS/2:6.0,6.00a;WINDOWS:1.0,1.5;WINDOWS NT:1.0,2.0,2.1,4.0,4.1,5.0
	Operating System(s): 
	Keyword(s): kbLangC kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC410 kbVC500
	Last Modified: 11-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 1.0, 1.5, 2.0, 2.1, 4.0, 4.1 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The C language does not internally support dynamic memory allocation for
	two-dimensional arrays. Creating such a structure requires some programming to
	set it up; however, once created the elements can be referred to by the familiar
	double bracket ([][]) notation. There is memory overhead involved in creating
	the structure. This technique is platform-independent working in the MS-DOS,
	Windows, Windows NT, and OS/2 operating systems.
	
	MORE INFORMATION
	================
	
	For the compiler to generate code for two-dimensional array element
	dereferencing, the number of columns of the array must be known at compile time.
	Therefore, it is possible to dynamically allocate a two-dimensional array if
	pointer declaration includes the "width" of the array. Below is a code fragment
	that illustrates this:
	
	  char (*array)[columns];
	
	  array = (char (*)[columns]) malloc(sizeof(char) * rows * columns);
	  if (array == NULL)
	  {
	      printf("Not enough memory!\n");
	      return;
	  }
	
	However, to give both dimensions of a two-dimensional array at run time the array
	must be dynamically allocated. In this case, a dynamically allocated
	two-dimensional array should be thought of as an array of one-dimensional
	arrays. There is some memory overhead, however, which requires allocation of an
	array of array pointers that is not necessary for statically defined
	two-dimensional arrays. Despite the overhead, each element of the two-
	dimensional arrays can be referenced with the bracket notation just as for a
	statically defined two-dimensional array.
	
	These are the steps for dynamically allocating a two-dimensional array:
	
	1. Declare a double dereferenced pointer of a desired type.
	
	2. Allocate the number of rows times the size of a pointer and assign the first
	  dereference to the beginning of this allocation.
	
	3. Loop through the rows and allocate the number of columns times the size of
	  the element.
	
	The structure conceptually resembles the following:
	
	  Array of                    Arrays of
	  Pointers                    Elements
	
	  ------     -------------------------                      -------
	  |    | -->|   |   |   |   |   |   |     . . . . . . .       |   |
	  ------     -------------------------                      -------
	  |    | -->|   |   |   |   |   |   |     . . . . . . .       |   |
	  ------     -------------------------                      -------
	  |    | -->|   |   |   |   |   |   |     . . . . . . .       |   |
	  ------     -------------------------                      -------
	  |    | -->|   |   |   |   |   |   |     . . . . . . .       |   |
	  ------     -------------------------                      -------
	        .
	        .
	        .
	        .
	        .    -------------------------                      -------
	  |    | -->|   |   |   |   |   |   |     . . . . . . .       |   |
	  ------     -------------------------                      -------
	  |    | -->|   |   |   |   |   |   |     . . . . . . .       |   |
	  ------     -------------------------                      -------
	
	Use _fmalloc() for MS-DOS and 16-Bit Windows to use the far/global heap. Note for
	Windows: _fmalloc() is available to be used when compiling with Microsoft C/C++
	compiler versions 7.0, 8.0, and 8.0c. Do not use GlobalAlloc and GlobalLock
	because this technique may use up too many selectors for relatively small
	allocations.
	
	Unlike a statically declared two-dimensional array, the rows are not contiguous
	with one another. But because this is an array of arrays it is possible to have
	a total structure larger than 64K without using huge pointers. If either the
	number of rows or the size of the rows is greater than 64K, then huge pointers
	are necessary.
	
	Sample Code
	-----------
	
	  /* Semi-pseudo code for a two-dimensional array of char's
	  * Note that this sample uses the far heap and uses far pointers.
	  * For 32-Bit Windows applications on Windows NT or Win32S or for
	  * OS/2, use malloc() and remove the _far keywords.
	  */ 
	
	     char _far * _far * array;
	     unsigned int i;
	     unsigned int rows, columns;  /* let's keep it within 64k */ 
	
	     /*  Set the rows and columns to desired dimensions. */ 
	     rows    = 8;
	     columns = 12;
	
	     array = (char _far * _far *) _fmalloc(sizeof(char _far *) * rows);
	     if (array == NULL)
	     {
	         printf("Not enough memory\n");
	         return;
	     }
	     for (i = 0; i < rows; i++)
	     {
	         array[i] = (char _far *) _fmalloc(sizeof(char) * columns);
	         if (array[i] == NULL)
	         {
	             printf("Not enough memory\n");
	             /* handle error, _free() the previously allocated rows */ 
	             return;
	         }
	     }
	
	     /* to use the array: array[row][column] */ 
	     array[0][1] = 'x';
	
	     /* etc.   */ 
	
	  * To Free the memory used by the array
	  **
	  */ 
	     for (i = 0; i< rows; i++)
	         _ffree(array[i]);
	     _ffree(array);
	
	Additional query words: kbinf halloc
	
	======================================================================
	Keywords          : kbLangC kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC410 kbVC500 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbvc150 kbvc100 kbVC410 kbVC500 kbVC200 kbVC210 kbVC32bitSearch kbVC500Search
	Version           : MS-DOS:6.0ax,7.0;OS/2:6.0,6.00a;WINDOWS:1.0,1.5;WINDOWS NT:1.0,2.0,2.1,4.0,4.1,5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
