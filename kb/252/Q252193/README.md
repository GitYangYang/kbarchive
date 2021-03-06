---
layout: page
title: "Q252193: POSIX-Based Program Leaks Private Bytes or Non Paged Pool Bytes"
permalink: /kb/252/Q252193/
---

## Q252193: POSIX-Based Program Leaks Private Bytes or Non Paged Pool Bytes

{% raw %}

	Article: Q252193
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbenv kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A POSIX-based program may leak Private Bytes and Non Paged Pool Bytes if the
	parent process uses the fork() function.
	
	CAUSE
	=====
	
	This problem can occur if the computer was not properly decrementing the
	process's Pool and Non-Paged Pool quota when the child process exited.
	
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
	
	  Date      Time                 Size    File name     
	  -------------------------------------------------------------
	  11/30/99  02:45p               952,960 Ntkrnlmp.exe
	  11/30/99  02:44p               932,736 Ntoskrnl.exe
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kb3rdparty kbenv kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
