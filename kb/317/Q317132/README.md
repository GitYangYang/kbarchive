---
layout: page
title: "Q317132: &quot;0x0000007F&quot; Err on Windows NT Server 4.0, Terminal Server Ed"
permalink: /kb/317/Q317132/
---

## Q317132: &quot;0x0000007F&quot; Err on Windows NT Server 4.0, Terminal Server Ed

{% raw %}

	Article: Q317132
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 18-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You may receive the following STOP error message on your Windows NT Server 4.0,
	Terminal Server Edition-based computer:
	
	  STOP: 0x0000007F (0x0000000F, 0x00000000, 0x00000000, 0x00000000)
	
	The Event Viewer may also show multiple purged print jobs.
	
	CAUSE
	=====
	
	This behavior can occur if both of the following conditions are true:
	
	- A Hewlett-Packard (HP) printer is installed on your system.
	
	  -and-
	
	- The HP printer uses the following driver:
	
	  HPBLAF2.DLL Thu Aug 12 12:18:53 1999
	
	To determine the version of your printer driver, follow these steps:
	
	1. Click Start, point to Settings, and then click Printers.
	
	2. Right-click the HP printer icon.
	
	3. On the shortcut menu, click Properties.
	
	4. Click the Device Options tab, and then click About.
	
	RESOLUTION
	==========
	
	To resolve this issue, browse to the following HP Web site to download the
	latest version of the printer driver:
	
	  http://www.hp.com/cposupport/software.html
	
	WORKAROUND
	==========
	
	To work around this issue, install an older or different version of the printer
	driver.
	
	NOTE: This workaround is not guaranteed to resolve this issue.
	
	MORE INFORMATION
	================
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbAudDeveloper kbWBTSearch kbWBTServ400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
