---
layout: page
title: "Q174230: Adding Duplicate Accounts May Cause A Memory Leak"
permalink: /kb/174/Q174230/
---

## Q174230: Adding Duplicate Accounts May Cause A Memory Leak

{% raw %}

	Article: Q174230
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Adding duplicate users and global groups from a trusted domain to local groups
	may cause excessive memory usage in Lsass.exe.
	
	CAUSE
	=====
	
	Lsass.exe fails to deallocate memory properly when an already existing imported
	user or group is re-added to one of the local groups. This problem will most
	likely occur when using a command-line utility to perform the add function.
	
	RESOLUTION
	==========
	
	To resolve this issue, perform one of the following:
	
	- If the Netlogon service is stopped and restarted, memory usage by Lsass.exe
	  returns to normal.
	
	  -or-
	
	- Install the updated version of Samsrv.dll.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0. A
	supported fix is now available, but has not been fully regression tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	Additional query words: usrmgr resources
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
