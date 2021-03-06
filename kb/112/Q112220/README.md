---
layout: page
title: "Q112220: PRB: System Resources Not Released While in FoxPro"
permalink: /kb/112/Q112220/
---

## Q112220: PRB: System Resources Not Released While in FoxPro

{% raw %}

	Article: Q112220
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.5,2.5a,2.5b,3.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 08-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	As you work in FoxPro for Windows, the amount of available system resources
	(User, System, and GDI memory) initially decreases. These system resources do
	not return to their original levels until after you have exited FoxPro.
	
	CAUSE
	=====
	
	FoxPro for Windows stores colors, pen types, font information, and brushes in
	memory. This is to make these items available as you are working. These items
	are swapped in and out of memory as necessary. Therefore, the memory decrease
	you may see during a FoxPro session relates more to caching than memory loss.
	
	NOTE: Even after exiting FoxPro for Windows, you may notice that GDI resources
	are lower than they were before FoxPro was loaded. This is not necessarily a
	problem with FoxPro. Some GDI objects may remain in memory even after a
	Windows-based application is closed. This means that a portion of the GDI heap
	may be lost until you restart Windows itself.
	
	MORE INFORMATION
	================
	
	For more information about Windows system resources, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q90762 Information on System Resources in Windows 3.0 & 3.1
	
	
	Additional query words: VFoxWin FoxWin 2.50 2.50a 2.50b
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro250 kbFoxPro250a kbFoxPro250b kbVFP300
	Version           : WINDOWS:2.5,2.5a,2.5b,3.0
	
	=============================================================================
	

{% endraw %}
