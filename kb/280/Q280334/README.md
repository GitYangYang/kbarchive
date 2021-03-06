---
layout: page
title: "Q280334: Problems Creating New File or Folder While Using NoDrives Policy"
permalink: /kb/280/Q280334/
---

## Q280334: Problems Creating New File or Folder While Using NoDrives Policy

{% raw %}

	Article: Q280334
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbenv kbtool kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you create a file or folder on the desktop after you have set the NoDrives
	policy, Explorer may stop responding (hang), and you may receive a stack
	overflow error message.
	
	CAUSE
	=====
	
	This problem can occur if Explorer receives two notifications that files or
	folders are created on or removed from the desktop while the NoDrives policy is
	in effect. Under these conditions, Explorer stops responding when it tries to
	update the folder tree.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date        Time    Size     File name     Platform
	  ---------------------------------------------------
	  04/03/2001  7:26pm  240,912  Explorer.exe  Intel
	  04/03/2001  7:22pm  396,560  Explorer.exe  Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	For additional information about how to restrict drive visibility by using the
	NoDrives policy, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q158457 Defining Local and Remote Drive Visibility Under Windows NT 4.0
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbtool kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
