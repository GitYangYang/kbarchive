---
layout: page
title: "Q67760: FIX: Bad Object File Generated with MASM 5.1 and 5.1a"
permalink: /kb/067/Q67760/
---

## Q67760: FIX: Bad Object File Generated with MASM 5.1 and 5.1a

{% raw %}

	Article: Q67760
	Product(s): Microsoft Macro Assembler
	Version(s): 5.1,5.1a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 5.1, 5.1a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The following mixed-language program does not assemble properly under the
	Microsoft Macro Assembler (MASM) version 5.1 and 5.1a.
	
	CAUSE
	=====
	
	The assembler does not generate the correct .OBJ record for the linker to
	resolve the reference properly. When the .EXE is built, the _test variable is
	located in the NULL segment instead of the _DATA segment; therefore, instead of
	the residing 1 byte apart, they are actually 42h bytes apart.
	
	RESOLUTION
	==========
	
	Removing the ASSUME statements from the assembly code eliminates the problem.
	These ASSUME statements are not necessary.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in MASM versions 5.1 and 5.1a. This
	problem was corrected in MASM version 6.0.
	
	MORE INFORMATION
	================
	
	Sample Code #1
	--------------
	
	  ; Assemble options needed: none
	
	          .model small, c
	
	          .data
	         ASSUME ds: nothing
	  PUBLIC xxx
	  xxx    DB 1
	         ASSUME ds: @data
	  PUBLIC yyy
	  yyy    DB 2
	
	         .code
	  PUBLIC func
	  func   PROC
	         MOV ax, OFFSET yyy
	         SUB ax, OFFSET xxx
	         RET
	  func   ENDP
	
	         END
	
	Sample Code #2
	--------------
	
	  /* Compile options needed: none
	  */ 
	
	  #include <stdio.h>
	  extern char xxx;
	  extern char yyy;
	
	  void main ()
	  {
	     printf( "C distance of yyy - xxx = %X\n", &yyy - &xxx );
	     printf( "MASM distance of yyy - xxx = %X\n", func () );
	  }
	
	Additional query words: 5.10 5.10a 6.00 buglist5.10 buglist5.10a fixlist6.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM510 kbMASM510a
	Version           : :5.1,5.1a
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
