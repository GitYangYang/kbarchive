---
layout: page
title: "Q72041: HOWTO: Using Device-Independent Bitmaps and Palettes"
permalink: /kb/072/Q72041/
---

## Q72041: HOWTO: Using Device-Independent Bitmaps and Palettes

{% raw %}

	Article: Q72041
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1,95; winnt:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbOSWinNT350 kbOSWinNT351 kbOSWinNT400 kbOSWin95 kbSDKWin16
	Last Modified: 16-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	- Microsoft Win32 Application Programming Interface (API), used with:
	   - Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	   - Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	   - Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The method Windows version 3.x uses to transfer colors from the color table of a
	Device-Independent Bitmap (DIB) to a Device-Dependent Bitmap (DDB) on a machine
	that supports palette operations depends on the value of the wUsage parameter
	specified in calls to the CreateDIBitmap or SetDIBits functions.
	
	Specifying DIB_RGB_COLORS matches the colors in the DIB color table to the
	logical palette associated with the Device Context (DC) listed in the function
	call.
	
	Specifying DIB_PAL_COLORS causes the entries in the DIB color table to not be
	treated as RGB values; instead, they are treated as word indexes into the
	logical palette associated with the DC listed in the function call.
	
	To create a device-dependent (displayable) bitmap from a DIB that retains the
	same colors, follow these five steps:
	
	1. Extract the colors from the DIB header.
	
	2. Use the CreatePalette function to make a logical palette with those colors.
	
	3. Use the SelectPalette function to select the logical palette into a device
	  context.
	
	4. Use the RealizePalette function to map the logical palette into the device
	  context.
	
	5. Call the CreateDIBitmap function using the device context that has the
	  logical palette selected.
	
	Because the CreateDIBitmap function creates a bitmap compatible with the device,
	to create a device-dependent monochrome bitmap from a DIB, call the CreateBitmap
	function with the desired width and height, specifying one color plane and one
	bit per pixel. Then call the SetDIBits function to render the image in the newly
	created monochrome bitmap.
	
	Additional query words: 3.00 3.10 3.50 4.00 win16sdk
	
	======================================================================
	Keywords          : kbOSWinNT350 kbOSWinNT351 kbOSWinNT400 kbOSWin95 kbSDKWin16 
	Technology        : kbAudDeveloper kbSDKSearch kbWin32sSearch kbWin32API kbWinSDKSearch
	Version           : WINDOWS:3.1,95; winnt:3.5,3.51,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
