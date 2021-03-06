---
layout: page
title: "Q120396: PRB: Image Functions Fail with Image Outside of Viewport"
permalink: /kb/120/Q120396/
---

## Q120396: PRB: Image Functions Fail with Image Outside of Viewport

{% raw %}

	Article: Q120396
	Product(s): Microsoft Fortran Compiler
	Version(s): 1.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FORTRAN PowerStation for MS-DOS, version 1.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The image functions SAVEIMAGE, SAVEIMAGE_W, LOADIMAGE, and LOADIMAGE_W fail when
	the specified image falls outside the current viewport. After SAVEIMAGE fails,
	calling GRSTATUS will return: $GRIMAGEREADERROR.
	
	CAUSE
	=====
	
	Though not documented, this behavior is by design. The functions listed above
	will fail when you attempt to place even part of an image outside the viewport.
	Images are never clipped to the viewport.
	
	RESOLUTION
	==========
	
	Do not attempt to place images outside of the current viewport. Either make the
	viewport larger or work with partial (smaller) images.
	
	STATUS
	======
	
	This behavior does occur with FORTRAN PowerStation 32.
	
	MORE INFORMATION
	================
	
	To demonstrate the problem, compile and run the sample program. The only bitmap
	file saved will be TEST.BMP, and the output will be:
	
	  Saving full viewport returns:           0
	  Saving outside viewport returns:         -1
	  Saving outside viewport GRSTATUS: $GRIMAGEREADERROR
	
	Sample Code
	-----------
	
	  C Compile options needed: none
	
	        include 'fgraph.fi'
	        include 'fgraph.fd'
	
	        integer*2 i, ret(3)
	
	        i = setvideomode($VRES16COLOR)
	        call setviewport(10,10,20,20)
	        ret(1) = saveimage("test.bmp",0,0,10,10)
	        ret(2) = saveimage("test2.bmp",0,0,10,11)
	        ret(3) = GRSTATUS()
	
	        i = setvideomode($DEFAULTMODE)
	
	        print *, "Saving full viewport returns:", ret(1)
	        print *, "Saving outside viewport returns:", ret(2)
	        if (ret(3) .eq. $GRIMAGEREADERROR)
	       +    print *, "Saving outside viewport GRSTATUS: $GRIMAGEREADERROR"
	
	        end
	
	Additional query words: 1.00 1.00a
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbFortranSearch kbZNotKeyword3 kbFORTRANPower100aDOS
	Version           : :1.0a
	
	=============================================================================
	

{% endraw %}
