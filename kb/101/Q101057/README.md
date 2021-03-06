---
layout: page
title: "Q101057: PRB: &quot;Variable Not Found&quot; or Public Variables Acting Private"
permalink: /kb/101/Q101057/
---

## Q101057: PRB: &quot;Variable Not Found&quot; or Public Variables Acting Private

{% raw %}

	Article: Q101057
	Product(s): Microsoft Fox Miscellaneous Products
	Version(s): MACINTOSH:2.01
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 23-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxBASE+ for Macintosh, version 2.01 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Adding memory variables to a report, or changing the scope of memory variables
	from private to public after a report is created, can cause a variety of
	problems in FoxBASE+/Mac, including the following:
	
	- Issuing a "Report Form XXX" command returns the error message
	
	  Variable not found
	
	  when you are using a report created with public memory variables.
	
	- Variables in a user-defined function (UDF) that were originally defined as
	  private may still function as private variables after the UDF is changed to
	  declare the variables as public.
	
	CAUSE
	=====
	
	When a report and environment is initially saved in FoxBASE+/Mac, a view file is
	created. The view file contains the memory variables currently defined in memory
	at the time the report is initially saved.
	
	Subsequent modifications to the defined memory variables are not saved in the
	view file, even if the environment is cleared and resaved. When the report form
	is printed, the view file restores memory to the state initially saved with the
	report. A variety of problems can occur, including memory variables appearing to
	be missing or being defined with an incorrect scope.
	
	RESOLUTION
	==========
	
	The following steps will resolve problems related to the view file:
	
	
	1. From the File menu, choose Open and select the report form. This will restore
	  memory to the state originally saved with the view file.
	
	2. Switch to the Command window. Make any necessary modifications to memory
	  variables (such as declaring new variables or releasing private memory
	  variables and declaring them as public).
	
	3. Switch to the View window. From the File menu, choose Save, and save the view
	  with the same name as the report.
	
	Additional query words: 2.01 errmsg err msg
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbHWMAC kbOSMAC kbAudDeveloper kbFoxproSearch kbFoxBASE201Mac kbFoxBASESearch
	Version           : MACINTOSH:2.01
	
	=============================================================================
	

{% endraw %}
