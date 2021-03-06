---
layout: page
title: "Q190043: PRB: Controls Collection vs. Standard Collection in For Each"
permalink: /kb/190/Q190043/
---

## Q190043: PRB: Controls Collection vs. Standard Collection in For Each

{% raw %}

	Article: Q190043
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0;
	Operating System(s): 
	Keyword(s): kbnokeyword kbVBp600 kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you remove controls from a Control collection in a For...Each loop, you
	might receive the following error:
	
	  Runtime error 735: The control is no longer usable because it has been
	  removed from the control collection.
	
	This occurs when you try to access the properties/methods of a control within the
	same loop that you are using to remove it from the collection.
	
	CAUSE
	=====
	
	When you remove an element from a standard VBA Collection object inside a loop,
	the iterator is updated automatically. Consequently, the collection is aware
	that the element has been removed, and will not attempt to access that member
	after it has been removed. The Controls collection for the Visual Basic Form
	object does not exhibit this behavior, and will fail with Runtime error 735 if
	you attempt to access the properties/methods of a control after it has been
	removed from the collection.
	
	RESOLUTION
	==========
	
	To avoid Runtime error 735, do one of the following:
	
	- Remove the unwanted item(s) from the Collection before iterating over it.
	
	- Use two separate iterations. One to remove the unnecessary elements, and the
	  other to access the collection elements. See step 4 in the MORE INFORMATION
	  section of this article for an example.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new Standard EXE project in Visual Basic.
	
	2. Copy the following code to the code module for Form1.
	
	        Private Sub Form_Load()
	           Dim x As Control
	           Dim y As Boolean
	
	           Controls.Add "vb.commandbutton", "a"
	           Controls.Add "vb.commandbutton", "b"
	           Controls.Add "vb.commandbutton", "c"
	           Controls.Add "vb.commandbutton", "d"
	           Controls.Add "vb.commandbutton", "e"
	           Controls.Add "vb.commandbutton", "f"
	           For Each x In Controls
	              Select Case x.Name
	                 Case "d", "e", "f"
	                 Controls.Remove x
	              End Select
	           Debug.Print x.Name
	           Next
	           End Sub
	
	3. Run the project. Runtime error 735 occurs.
	
	4. Replace the code from step 2 with the following code.
	
	  NOTE: This code uses two separate iterations to accomplish the task. Because
	  you can remove Control Collection elements by name, another alternative is to
	  remove the controls without using a loop.
	
	        Private Sub Form_Load()
	           Dim x As Control
	           Dim y As Boolean
	
	           Controls.Add "vb.commandbutton", "a"
	           Controls.Add "vb.commandbutton", "b"
	           Controls.Add "vb.commandbutton", "c"
	           Controls.Add "vb.commandbutton", "d"
	           Controls.Add "vb.commandbutton", "e"
	           Controls.Add "vb.commandbutton", "f"
	           For Each x In Controls
	              Select Case x.Name
	                 Case "d", "e", "f"
	                 Controls.Remove x
	              End Select
	           Next
	           For Each x In Controls
	              Debug.Print x.Name
	           Next
	
	        End Sub
	
	5. Run the project.
	
	RESULT: The names of the remaining controls appear in the Immediate window.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnokeyword kbVBp600 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0;
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
