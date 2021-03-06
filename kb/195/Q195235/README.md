---
layout: page
title: "Q195235: BUG: Caret Disappears After Tabbing From a Windowless TextBox"
permalink: /kb/195/Q195235/
---

## Q195235: BUG: Caret Disappears After Tabbing From a Windowless TextBox

{% raw %}

	Article: Q195235
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbCtrl kbVBp kbVBp600bug kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you shift focus from a Windowless TextBox on a Windowless UserControl to a
	standard TextBox on a form, the caret is not visible in the form's TextBox. The
	form's TextBox has the focus and the keyboard input will be directed to the
	TextBox, but the caret is not present.
	
	RESOLUTION
	==========
	
	Resolution #1
	-------------
	
	Set the Windowless property of the UserControl to False.
	
	Resolution #2
	-------------
	
	Invoke the SetFocus method in the GotFocus event of the TextBox. For example:
	
	     Private Sub Text1_GotFocus()
	        Me.SetFocus
	     End Sub
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a Standard EXE project in Visual Basic. Form1 is created by default.
	
	2. Choose Components from the Project menu, check "Microsoft Windowless Controls
	  6.0," and click OK.
	
	3. From the Project menu, add a new UserControl to the project.
	
	4. Set the Windowless property of the UserControl to True.
	
	5. Add a Windowless TextBox to the UserControl.
	
	6. Close the UserControl window, and add an instance of the UserControl to
	  Form1.
	
	7. Add a standard TextBox to Form1.
	
	8. Run the project. The caret should appear in the UserControl's TextBox.
	
	9. Press the TAB key, or click on the form's Textbox. Note that the caret does
	  not appear, although the TextBox will accept keyboard input.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q189950 HOWTO: Install the Microsoft Windowless Controls for VB6
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCtrl kbVBp kbVBp600bug kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
