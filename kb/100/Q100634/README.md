---
layout: page
title: "Q100634: HOWTO: Specify Shared and Nonshared Data in a DLL"
permalink: /kb/100/Q100634/
---

## Q100634: HOWTO: Specify Shared and Nonshared Data in a DLL

{% raw %}

	Article: Q100634
	Product(s): Microsoft C Compiler
	Version(s): 2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbDLL kbKernBase kbLangC kbVC kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kbVC420 kbVC500 k
	Last Modified: 26-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 2.0, 2.1, 2.2, 4.0, 4.1 
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	NOTE: Microsoft Visual C++ NET (2002) supported both the managed code model that is provided by the .NET Framework and the unmanaged native Windows code model. The information in this article applies to unmanaged Visual C++ code only.
	
	SUMMARY
	=======
	
	To have both shared and non-shared data in a Dynamic Link Library (DLL) which is
	built with a 32-bit Microsoft C compiler, you need to use the #pragma data_seg
	directive to set up a new named section. Then you must inform the linker of the
	correct sharing attributes for this new named data section using either the .def
	file or a linker switch.
	
	The system tries to load the shared memory block created by #pragma data_seg at
	the same address in each process. However, if the block cannot be loaded into
	the same memory address, it is mapped to a different address, but it is still
	shared.
	
	NOTE: If the block contains pointers, this can be a problem. If the pointer holds
	the address of a variable not in the shared data segment, this address is valid
	only in one process space. If the address is in the shareddata segment, it will
	be valid as long as the above relocation does not occur. Because this is
	unreliable, you should not use pointers. You can use arrays in a shared data
	segment, but do so with caution. The array name is a pointer. Do not pass this
	value between processes. For example, if you have a string declared in the
	shared data segment as char Customer[20] = {0}, it is okay for each process to
	use that variable name, as in strcpy(buf, Customer) or char FirstInitial =
	Customer[0]. However, do not pass the value of Customer to another process as in
	PostMessage(hwndNotMyWindow, WM_USER, 0, (LPARAM)Customer).
	
	It is not recommended to use pointers or arrays in the shared data segment,
	because relocation can break the sharing between processes. If you must use
	them, you can minimize the chances of seeing this relocation if you
	intentionally change the preferred base address of the DLL. You can do this by
	using the Rebase.exe utility, or you can use the /BASE linker switch when
	building the image with Visual C++. If you don't change the preferred base
	address, you may see output during debugging that resembles the following:
	
	  
	
	  LDR: Dll NAME.DLL base 10000000 relocated due to collision with
	  [path to another DLL].
	
	You may also see that the DLL has been relocated due to dynamically allocated
	memory. If you modify each of your DLLs to have a unique preferred base address,
	you will minimize the chances of relocation. You also should use the suggested
	address ranges listed in the documentation for the ReBaseImage API.
	
	MORE INFORMATION
	================
	
	Below is a sample of how to define a named data section in your DLL. The first
	line directs the compiler to include all the data declared in this section in
	the .MYSEC data segment. This means that the iSharedVar variable would be
	considered part of the .MYSEC data segment. By default, data is nonshared.
	
	Note that you must initialize all data in your named section. The data_seg pragma
	only applies to initialized data.
	
	The third line below, "#pragma data_seg()", directs the compiler to reset
	allocation to the default data section.
	
	Sample Code
	-----------
	
	     #pragma data_seg(".MYSEC")
	     int iSharedVar = 0;
	     #pragma data_seg()
	
	You must also tell the linker that the variables in the section you defined are
	to be shared by modifying your .def file to include a SECTIONS section or by
	specifying /SECTION:.MYSEC,RWS in your link line. For example, aSECTIONS section
	could look like:
	
	     SECTIONS
	
	       .MYSEC   READ WRITE SHARED
	
	Alternatively, some compilers allow you to set the linker switch in your code so
	that if your file is ever copied to another project, the linker switch goes with
	it. To do this, include the following line in your code preferably near the
	#pragma data_seg(".MYSEC") line:
	
	     #pragma comment(linker, "/SECTION:.MYSEC,RWS")
	
	Be careful not to include any extraneous spaces inside the quotation marks
	because this may cause the linker to misinterpret the directive.
	
	NOTE: By convention, each section name begins with a period. (The period is not
	required.) All section names must not be longer than eight characters, including
	the period character.
	
	Additional query words: memory mapped win95 winnt nt40
	
	======================================================================
	Keywords          : kbDLL kbKernBase kbLangC kbVC kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kbVC420 kbVC500 kbVC600 kbDSupport kbGrpDSKernBase 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbVC220 kbVC410 kbVC420 kbVC500 kbVC600 kbVC200 kbVC210 kbVC32bitSearch kbVC500Search
	Version           : :2.0,2.1,2.2,4.0,4.1,4.2,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
