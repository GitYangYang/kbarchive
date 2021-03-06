---
layout: page
title: "Q172244: BUG: VBComponents Add Method Cannot Add a Form"
permalink: /kb/172/Q172244/
---

## Q172244: BUG: VBComponents Add Method Cannot Add a Form

{% raw %}

	Article: Q172244
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When attempting to add a Form to a Visual Basic 5.0 project through the
	IDTExtensibility model with VBComponents' Add method and passing
	vbext_ct_MSForm, you get Run-time error '-2147467259 (800004005)':
	
	  "System Error &h80004005(-2147467259). Unspecified error"
	
	CAUSE
	=====
	
	Visual Basic 5.0 does not support Forms3 designers, enum member vbext_ct_MSForm
	is not valid.
	
	RESOLUTION
	==========
	
	Use VBComponents' AddFromTemplate method. See the MORE INFORMATION Section of
	this article.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start a New AddIn Project in Visual Basic 5.0.
	
	2. Add the following line to the Private Sub OKButton_Click() in frmAddIn:
	
	        VBInstance.VBProjects(1).VBComponents.Add (vbext_ct_MSForm)
	
	3. Type "ADDTOINI" in the Immediate (debug) window and press the ENTER key.
	
	4. Press the F5 key to run the project.
	
	5. Start another instance of Visual Basic with a new standard EXE project*.
	
	6. Under Add-Ins menu, select Add-In Manager, and then select My AddIn from the
	  list.
	
	7. Under Add-Ins menu, select My AddIn item.
	
	8. Click OK on the Add-In Form. You will get:
	
	  Run-time error '-2147467259 (800004005)': System Error
	  &h80004005(-2147467259). Unspecified error.
	
	9. Add a new form to the add-in project and save it in the 'Template' folder
	  under Visual Basic folder as Form1.frm (for example, 'C:\Program
	  Files\DevStudio\VB\Template', and then remove the form from the project.
	
	10. Change the code:
	
	        VBInstance.VBProjects(1).VBComponents.Add (vbext_ct_MSForm)
	
	  in step 6 to:
	
	        VBInstance.VBProjects(1).VBComponents.AddFromTemplate _
	        ("C:\Program Files\DevStudio\VB\Template\Form1.frm")
	
	11. Repeat steps 3 through 8. This time a form should be added to your project
	  each time you click OK.
	
	* If your project does not have a form, you will get 'Run-time error #9,
	subscript out of range.'
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp500 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbZNotKeyword3
	Version           : 5.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
