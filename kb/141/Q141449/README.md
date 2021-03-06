---
layout: page
title: "Q141449: BUG: Drag &amp; Drop From DE to Grid Causes Error or FoxPro Quits"
permalink: /kb/141/Q141449/
---

## Q141449: BUG: Drag &amp; Drop From DE to Grid Causes Error or FoxPro Quits

{% raw %}

	Article: Q141449
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b
	Operating System(s): 
	Keyword(s): kbbuglist
	Last Modified: 08-JAN-2000
	
	3.00 3.00b
	WINDOWS
	kbtool kbbuglist
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You drag a field from a form's data environment to a grid you are editing and an
	error occurs that gives the following message:
	
	  Parent object will not allow this property setting for
	  Formset1.Form1.Grid1.Column1.Text1.ControlSource.
	
	  -or-
	
	  This program has performed an illegal operation and will be shut down. If the
	  problem persists, contact the program vendor.
	
	NOTE: the error wording is from Windows 95. In other versions of Windows, a
	general protection (GP) fault occurs with different wording.
	
	The first error occurs if:
	
	- You drop the field on an exposed column in the grid and you are using Visual
	  FoxPro version 3.0 for Windows.
	
	- You drop the field on any part of the grid and you are using Visual FoxPro
	  version 3.0b for Windows.
	
	The second error occurs if you drop the field on the area of the grid other than
	an exposed column and you are using Visual FoxPro version 3.0 for Windows.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	Drag and drop succeeds in placing the TextBox object into the exposed column but
	does not allow the ControlSource to be set.
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Create a new form, and place a grid on the form from the Form Designer
	  toolbar. Set the grid's ColumnCount property to 1.
	
	2. Right-click the form, and select Data Environment. Then right-click the Data
	  Environment window, and select Add.
	
	3. Select a table and add it to the Data Environment.
	
	4. Right-click the grid, and select Edit.
	
	5. Drag a field from the table in the Data Environment, and drop it on the
	  exposed column in the grid. At this point, the first error occurs. If you
	  examine the Column in the Property Sheet Object list box, you may note the
	  added text box is now present but the ControlSource property for that text
	  box is not set.
	
	6. Drag a field from the table in the Data Environment, and drop it anywhere on
	  the grid other than the exposed column. At this point, the second error (a GP
	  fault) occurs in Visual FoxPro version 3.0 for Windows.
	
	Additional query words: buglist3.00 buglist3.00b kbvfp300 kbvfp300b
	
	======================================================================
	Keywords          :  kbbuglist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b
	Version           : WINDOWS:3.0,3.0b
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
