---
layout: page
title: "Q47961: INFO: Extracting Function ptr from a Variable arg List Function"
permalink: /kb/047/Q47961/
---

## Q47961: INFO: Extracting Function ptr from a Variable arg List Function

{% raw %}

	Article: Q47961
	Product(s): Microsoft C Compiler
	Version(s): 1.0,1.5,2.0,2.1,4.0,5.0
	Operating System(s): 
	Keyword(s): kbcode kbLangC kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500 kbVC600
	Last Modified: 13-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft C for MS-DOS 
	- Microsoft C/C++ for MS-DOS 
	- Microsoft Visual C++, versions 1.0, 1.5, 2.0, 2.1, 4.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In Microsoft C the va_arg() macro may be used to remove an item from a variable
	argument list. When the element to be removed is complex, however, you may have
	to typedef the item type. This is necessary because the va_arg() macro requires
	you to provide the type of the item to be removed from the list. For a pointer
	to a function, if you were to put the item type (the declaration of the function
	ptr) as follows:
	
	     FuncPtr = va_arg (arg_list, (int(*)(void)) );
	
	The compiler would yield the following error:
	
	     C2059: Syntax Error : ')'
	
	You could try to get around this by grabbing the function pointer as a data
	pointer, and then typecasting it to a function pointer, as in the following
	line:
	
	     FuncPtr = (int (*)(void)) va_arg (arg_list, char *);
	
	This will work; however, you will get the following warning:
	
	  C4074: Non-standard extension used, cast of data pointer to function pointer
	
	The best solution is to typedef the function pointer. With a typedef, you avoid
	both the error and the warning.
	
	MORE INFORMATION
	================
	
	The following sample code passes a function pointer to a variable argument list
	function, changes that pointer, and returns it to the calling procedure. To
	implement this, however, you need to pass the function pointer by reference. For
	this reason, a pointer is typedef'd to a function pointer. Once in the variable
	argument list function, the pointer is dereferenced to the function pointer to
	get at the actual function pointer.
	
	Sample Code
	-----------
	
	  #include <stdio.h>
	  #include <stdarg.h>
	
	  typedef void (*FuncPtr)(void);
	  typedef FuncPtr *PFuncPtr;
	
	  void hello(void);
	  void varfunc(int, ...);
	
	   FuncPtr func1, func2;
	   int i;
	
	  void main(void)  {
	      func1 = hello;
	      printf ("Function pointer: func1 now points to Hello()\n");
	      printf ("About to use func1 to make a call to Hello()\n\n");
	      func1();
	      printf ("Now lets pass these function pointers to our variable");
	      printf (" argument list\n");
	      varfunc(2, &func1, &func2);   /* To alter ptr, pass by reference */ 
	      printf ("\nAfter the call to the variable argument procedure,\n");
	      printf ("function pointer: func2 now points to Hello()\n");
	      printf ("About to use func2 to make a call to Hello()\n\n");
	      func2();
	   }
	
	  void hello(void)  {
	      printf ("Hello, I'm in the procedure HELLO()\n");
	   }
	
	  void varfunc(int i, ...)  {
	      va_list arg_ptr;
	      PFuncPtr tmpfptr;                /* Temporary ptr to function ptr
	  */ 
	
	      printf ("\nIn function VARFUNC\n");
	      va_start (arg_ptr, i);
	      printf ("%d arguments were passed\n", i);
	      tmpfptr = va_arg (arg_ptr, PFuncPtr);  /* Grab pointer to fnptr */ 
	      *tmpfptr = hello;                      /* Assign fnptr addr of fn
	  */ 
	      tmpfptr = va_arg (arg_ptr, PFuncPtr);  /* Grab pointer to fnptr */ 
	      *tmpfptr = hello;                      /* Assign fnptr addr of fn
	  */ 
	   }
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbLangC kbVC100 kbVC150 kbVC200 kbVC210 kbVC400 kbVC500 kbVC600 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbZNotKeyword8 kbvc150 kbvc100 kbCCompSearch kbZNotKeyword3 kbVC500 kbVC200 kbVC210 kbVC32bitSearch kbVC500Search
	Version           : :1.0,1.5,2.0,2.1,4.0,5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
