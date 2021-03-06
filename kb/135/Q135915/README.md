---
layout: page
title: "Q135915: PRB: BackColor for Objects in a Grid Appears to Be Incorrect"
permalink: /kb/135/Q135915/
---

## Q135915: PRB: BackColor for Objects in a Grid Appears to Be Incorrect

{% raw %}

	Article: Q135915
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Under certain conditions, you may find that the BackColor of an object contained
	within a grid appears to be incorrect.
	
	CAUSE
	=====
	
	this occurs if the BackStyle property of the object is set to Transparent, and
	the BackColor of the grid differs from that of the form on which it resides. An
	object contained within a grid inherits the BackColor of the form when the
	object's BackStyle property is set to Transparent.
	
	RESOLUTION
	==========
	
	Set the BackColor of the Object to the same value used by the grid.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Open or switch to Microsoft Visual FoxPro, and open any table into the active
	  work area.
	
	2. Type CREATE FORM TEST in the Command window, and press ENTER.
	
	3. Using the Property Window of the form, set the BackColor of the form to
	  255,0,0 to make the form's background color red.
	
	4. Place a grid on the form. Using the Property Window, set the ColumnCount
	  property of the grid to 2.
	
	5. Using the Property Window, set the BackStyle property of Text1 in Column1 of
	  the grid to Transparent.
	
	6. Using the Property Window, set the Sparse property of Column 1 to false
	  (.F.).
	
	7. Save and run the Form. Note that Column 1 of the grid is Red because it is
	  inheriting the BackColor Property of the form rather than the grid as
	  expected.
	
	Additional query words: 3.00 VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
