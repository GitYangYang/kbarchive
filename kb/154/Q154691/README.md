---
layout: page
title: "Q154691: XCLN: How to Print the Schedule+ Contact List in Two Columns"
permalink: /kb/154/Q154691/
---

## Q154691: XCLN: How to Print the Schedule+ Contact List in Two Columns

{% raw %}

	Article: Q154691
	Product(s): Microsoft Schedule+ for Windows
	Version(s): WINDOWS:7.0
	Operating System(s): 
	Keyword(s): kbprint kbPrinting
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Schedule+ for Windows, version 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you print a Contact List in Microsoft Schedule+, the list is printed in one
	left-aligned column. This format leaves a lot of empty space on the right side
	of the page. There is no way to change this format through the user interface.
	
	CAUSE
	=====
	
	This behavior is by design of Microsoft Schedule+.
	
	WORKAROUND
	==========
	
	To work around this problem, you can edit the associated Print Layout (.PRT)
	file to allow you to print in two columns. (However, Microsoft does not support
	the modifying of the .PRT files.)
	
	The .PRT files, located in the \Msoffice\Schedule folder, control the layout of
	printed Schedule+ views. These are ASCII (text) files, which you can edit in a
	text editor such as Notepad.
	
	WARNING: Microsoft does not support .PRT files that have been modified. Therefore
	you should make a copy of the original file to retain access to the original
	format in the Print dialog box in Schedule+.
	
	The .PRT file that controls the layout of the Contact List is named Card1.prt. To
	be able to print the Contact List in either one or two column format, follow
	these steps:
	
	1. Copy the Card1.prt file.
	
	  a. In the Windows Explorer, locate the card1.prt file. By default this file
	     is in the following directory:
	
	  Program Files\Microsoft Office\Office
	
	  b. Use the right mouse button to click (right-click) the Card1.prt file, and
	     then click Copy on the shortcut menu.
	
	  c. Click once on an empty area of the folder contents, and choose Paste from
	     the Edit menu.
	
	  NOTE: The pasted file is named "Copy of card1.prt."
	
	2. Open "Copy of card1.prt" in a text editor such as Notepad.
	
	3. Change the first line to read:
	
	     VIEW "Contact List - 2 columns","FULL page",ALL,,1000,1000
	
	  NOTE: Quotation marks and commas are required for proper functionality.
	
	4. Scroll down to the first Contact List section, and replace the contents of
	  this section with the following text, beginning at the first line.
	
	  NOTE: Be sure to make all modifications exactly as printed here due to case
	  sensitivity.
	
	        OBJECT   ,RECTANGLE,0,70,1000,74
	           OPTIONS     BLACK
	
	        OBJECT   ,RECTANGLE,0,74,500,978
	
	        OBJECT  ,TEXT,10,75,1000,120
	           STYLES      styHeading
	           VALUE       "Contact List:"
	
	        OBJECT  ,CARDLIST,0,75,500,978
	           STYLES      styApptText, styListHeading, styProjectText
	
	        OBJECT   ,OVERFLOW,10,115,1000,978
	           OPTIONS     FULL, NONE, 0
	
	        OBJECT   ,RECTANGLE,500,74,1000,978
	
	        OBJECT   ,OVERFLOW,510,115,1000,978
	           OPTIONS     FULL, NONE, 0
	
	5. Scroll down to the second Contact List section, and replace the contents of
	  this section with the following text, beginning at the first line.
	
	  NOTE: Be sure to make all modifications exactly as printed here due to case
	  sensitivity.
	
	        OBJECT   ,RECTANGLE,0,70,1000,74
	           OPTIONS     BLACK
	
	        OBJECT   ,RECTANGLE,0,74,500,978
	
	        OBJECT  ,TEXT,10,75,1000,120
	           STYLES      styHeading
	           VALUE       "Contact List (continued):"
	
	        OBJECT   ,RECTANGLE,500,74,1000,978
	
	        OBJECT   ,OVERFLOW,10,115,1000,978
	           OPTIONS     FULL, NONE, 0
	
	        OBJECT   ,OVERFLOW,510,115,1000,978
	           OPTIONS     FULL, NONE, 0
	
	6. Save the file as a text only document.
	
	In the Print Layout section of the Print dialog box, there are now two entries
	for the Contact List, the original (Contact List) and the copy (Contact List - 2
	columns).
	
	If you choose Contact List - 2 columns, Schedule+ prints the Contact List in two
	columns.
	
	MORE INFORMATION
	================
	
	For the most part, .PRT files are formatted in sections. The exception is the
	very first line of the file which defines a view.
	
	Section names differ depending on the type of printout required. For example, the
	card1.prt file contains the following sections.
	
	Header - Username
	-----------------
	
	This section defines the Header for the first page.
	
	Contact List
	------------
	
	This section defines the information to be printed on the first page.
	
	Footer - Text and Page num.
	---------------------------
	
	This section defines the footer of the first page.
	
	PAGE 2 - Overflow page
	----------------------
	
	This section defines a new or overflow page if the printout spans more than one
	page.
	
	Header - Username
	-----------------
	
	This section defines the header for the second and subsequent pages.
	
	Contact List
	------------
	
	This section defines the information to be printed on the second and subsequent
	pages.
	
	Footer - Text and Page num.
	---------------------------
	
	This section defines the footer for the second and subsequent pages
	
	Additional query words: 7.0
	
	======================================================================
	Keywords          : kbprint kbPrinting 
	Technology        : kbScheduleSearch kbSchedule700
	Version           : WINDOWS:7.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
