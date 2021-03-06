---
layout: page
title: "Q245128: Restrict Remote Access to Event Viewer on Windows NT Server."
permalink: /kb/245/Q245128/
---

## Q245128: Restrict Remote Access to Event Viewer on Windows NT Server.

{% raw %}

	Article: Q245128
	Product(s): Microsoft Windows NT
	Version(s): 2000,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows 2000 Professional 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to edit the registry to restrict remote access to
	Event Viewer on a computer running Microsoft Windows NT Server 4.0 or Windows
	2000.
	
	MORE INFORMATION
	================
	
	IMPORTANT: This article contains information about modifying the registry.
	Before you modify the registry, make sure to back it up and make sure that you
	understand how to restore the registry if a problem occurs. For information
	about how to back up, restore, and edit the registry, click the following
	article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	To restrict remote access to Event Viewer to only the Administrators group:
	
	1. At the computer on which you want to restrict remote access to Event Viewer,
	  use Registry Editor (Regedt32) to locate the following registry key:
	
	<B>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\SecurePipeServers\Winreg\AllowedPaths</B>
	
	2. Double-click the Machine value in the right pane. Delete the following
	  string:
	
	  System\CurrentControlSet\Services\Eventlog
	
	  NOTE: Be careful to leave the remaining strings in place.
	
	3. Quit Registry Editor.
	
	4. Restart the computer.
	
	To permit users other than members of the Administrators group to have remote
	access to Event Viewer:
	
	1. Create a global group in the domain, and then add the appropriate user
	  accounts to this group.
	
	2. Use Registry Editor (Regedt32) to locate the Winreg registry key.
	
	3. Click the Winreg key, and then click Permissions on the Security menu.
	
	4. In the Registry Key Permissions dialog box, click Add.
	
	5. In the Add Users And Groups dialog box, click the name of the global group,
	  and then click Add.
	
	6. In the Type Of Access box, click the appropriate type, and then click OK.
	
	7. To close the Registry Key Permissions dialog box, click OK.
	
	8. Quit Registry Editor.
	
	9. Restart the computer.
	
	Additional query words: edit registry
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbwin2000Search kbwin2000ProSearch kbwin2000Pro
	Version           : :2000,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
