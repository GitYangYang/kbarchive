---
layout: page
title: "Q47760: The _QC Predefined Preprocessing Macro"
permalink: /kb/047/Q47760/
---

## Q47760: The _QC Predefined Preprocessing Macro

{% raw %}

	Article: Q47760
	Product(s): See article
	Version(s): 1.00 1.01 2.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | S_C S_QuickASM | mspl13_c
	Last Modified: 10-OCT-1989
	
	The _QC macro is automatically defined when compiling with QuickC and
	undefined when compiling with Microsoft C Optimizing Compiler. This
	predefined macro can be used to conditionally compile parts of code
	that are unique to one compiler or another. For example, if inline
	assembly is used in an application program, it might be a good idea to
	check the condition of _QC macro before compiling that section of
	code, as follows:
	
	#ifdef _QC      /* check to see if compiling in QuickC */
	
	#define _enable()  _asm { sti }
	#define _disable() _asm { cli }
	
	#endif
	
	This macro was not documented in the QuickC manuals or in the
	README.DOC. Support for this macro is not guaranteed in future
	releases of the QuickC product.

{% endraw %}
