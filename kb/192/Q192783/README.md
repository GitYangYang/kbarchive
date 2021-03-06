---
layout: page
title: "Q192783: BUG: PDW Does Not Include CLSID in Default HTML Page for IE 3.X"
permalink: /kb/192/Q192783/
---

## Q192783: BUG: PDW Does Not Include CLSID in Default HTML Page for IE 3.X

{% raw %}

	Article: Q192783
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbwizard kbActiveDocs kbAppSetup kbVBp kbVBp600
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Package and Deployment Wizard- (PDW) generated HTML page for IE 3.x will not
	contain the CLSID for an ActiveX Document EXE.
	
	RESOLUTION
	==========
	
	Use REGEDIT to determine CLSID for your project and manually enter the CLSID in
	the PDW generated HTML page.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start Visual Basic 6.0 and select ActiveX Document EXE.
	
	2. Save the project as follows:
	
	  "C:\Test\project1.vbp"
	
	3. Start the Visual Basic 6.0 Package and Deployment Wizard, click the "Package"
	  button, and compile the project.
	
	4. Select "Internet Package," and go through to the "Finished" step using the
	  default options.
	
	5. Click "Finish," and then generate the setup program.
	
	  Result:
	
	  The generated PDW HTML page does not contain CLSID as shown in the example
	  below:
	
	        <HTML>
	        <HEAD>
	        <TITLE>YourProject.CAB</TITLE>
	        </HEAD>
	        <BODY>
	
	        <a href=UserDocument1.VBD>UserDocument1.VBD</a>
	        <!--*********** Comment Begin **********
	         Internet Explorer Version 3.x HTML
	         ====================================
	         The following HTML code has been commented
	         out and provided for ActiveX User Documents
	         download support in IE 3.x only. This
	         HTML script may not work properly in later
	         versions of Internet Explorer.
	
	         Additional information about downloading
	         ActiveX User Documents in IE 3.x can be
	         found in Microsoft's Online support on the
	         internet at http://support.microsoft.com.
	         *********** Comment End   ********** -->
	
	        <!--*********** Comment Begin **********
	        <HTML>
	        <OBJECT ID="UserDocument1"
	        CLASSID="CLSID:"
	        CODEBASE="g1.CAB#version=1,0,0,0">
	        </OBJECT>
	
	        <SCRIPT LANGUAGE="VBScript">
	        Sub Window_OnLoad
	         Document.Open
	         Document.Write "<FRAMESET>"
	         Document.Write "<FRAME SRC=""UserDocument1.VBD"">"
	         Document.Write "</FRAMESET>"
	         Document.Close
	        End Sub
	        </SCRIPT>
	        </HTML>
	         *********** Comment End   ********** -->
	
	        </BODY>
	        </HTML>
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q190046 : INFO: VB6 Readme Part 6 - Wizard Issues
	
	======================================================================
	Keywords          : kbwizard kbActiveDocs kbAppSetup kbVBp kbVBp600 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
