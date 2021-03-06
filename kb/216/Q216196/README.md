---
layout: page
title: "Q216196: PRB: Text Output Parameter Empty with Unicode Build"
permalink: /kb/216/Q216196/
---

## Q216196: PRB: Text Output Parameter Empty with Unicode Build

{% raw %}

	Article: Q216196
	Product(s): Microsoft C Compiler
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbDatabase kbMFC kbODBC kbVC500 kbVC600 kbGrpDSVCDB
	Last Modified: 18-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After calling a stored procedure that has a Varchar (Text) output parameter, no
	errors are thrown, but the variable that holds the output is always null. This
	problem only happens in Unicode builds.
	
	Standard builds work after the solution provided by the following article in the
	Microsoft Knowledge Base has been implemented:
	
	  Q182386 PRB: Varchar Output Parameter Causes "Data Truncated" Error
	
	Note that text output parameters do not work at all unless the workaround in that
	article has been implemented.
	
	CAUSE
	=====
	
	The cause is a bug in the Unicode section of the RFX_Text function. The Unicode
	section in the RFX_TextOut function is setting up a Proxy parameter, binding the
	real parameter to the proxy parameter, and then allocating new memory to the
	real parameter. The data is getting put into the bound proxy parameter
	correctly, but it's not getting transfered to the data member.
	
	RESOLUTION
	==========
	
	The resolution is in two parts:
	
	1. You must implement the workaround provided in the following Knowledge Base
	  article:
	
	  Q182386 PRB: Varchar Output Parameter Causes "Data Truncated" Error
	
	  Without implementing this workaround, the text output parameters will not work
	  in either Standard or Unicode builds.
	
	2. You must move the data from the proxy parameter to the data member yourself.
	
	For example, assume we have one varchar output parameter and that we have
	implemented the code suggested in the Microsoft Knowledge Base article Q182386
	in a function called RFX_TextOut. Assuming we have a CRecordset named
	RSTestTextOut that contains a CString data member called strTextOut that will
	hold the data, you would implement the workaround as follows:
	
	  // Call our stored procedure.
	  RSTestTextOut.Open(CRecordset::forwardOnly, _T("{CALL YourSP(?)}"), CRecordset::readOnly);
	
	  //Assign the proxy parameter to our CString variable.
	  RSTestTextOut.strTextOut = (char*)RSTestTextOut.m_pvParamProxy[0];
	
	Our variable strTextOut now holds the value of the output parameter returned from
	the stored procedure. If you wanted to be more strict, you could wrap that in an
	#ifdef _UNICODE ... #endif section, because it's only needed in Unicode builds.
	Of course, if you had more than one varchar output parameter, you would need a
	similar line for each parameter, such as:
	
	  RSTestTextOut.strTextOut2 = (char*)RSTestTextOut.m_pvParamProxy[1];
	
	REFERENCES
	==========
	
	For additional information about Text parameters in Unicode builds, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q182386 PRB: Varchar Output Parameter Causes "Data Truncated" Error
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDatabase kbMFC kbODBC kbVC500 kbVC600 kbGrpDSVCDB 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC600 kbVC32bitSearch kbVC500Search
	Version           : :5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
