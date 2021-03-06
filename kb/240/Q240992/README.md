---
layout: page
title: "Q240992: Err Msg: An Application Error Has Occurred and an Application..."
permalink: /kb/240/Q240992/
---

## Q240992: Err Msg: An Application Error Has Occurred and an Application...

{% raw %}

	Article: Q240992
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you log on to a computer running Terminal Server Edition, you may receive
	the following error message:
	
	  An application error has occurred and an application error log is being
	  generated.
	  Userinit.exe
	  Exception: access violation (0xc0000005), Address: 0x77f901b3
	
	NOTE: The address value may be different, depending on your computer
	configuration.
	
	The Terminal Server client is disconnected after you click OK or Cancel.
	
	CAUSE
	=====
	
	This behavior occurs because an invalid value exists in the registry.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To work around this issue, delete the invalid registry value:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the following registry key:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Terminal
	  Server\Install\IniFile Times
	
	3. Locate the invalid value (this is usually a value with no name).
	
	4. Click the invalid value.
	
	5. On the Edit menu, click Delete, and then click Yes.
	
	6. Quit Registry Editor.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article. This problem was first corrected in
	Windows NT 4.0 Server, Terminal Server Edition, Service Pack 5.
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
