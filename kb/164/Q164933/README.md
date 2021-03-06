---
layout: page
title: "Q164933: How to Allow Poolmon.exe to Run by Setting GlobalFlag Value"
permalink: /kb/164/Q164933/
---

## Q164933: How to Allow Poolmon.exe to Run by Setting GlobalFlag Value

{% raw %}

	Article: Q164933
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	The utility Poolmon.exe located on the Windows NT CD-ROM can be used to track
	memory usage in both paged and nonpaged pools of memory. When POOLMON is run
	from the command prompt of Windows NT, the following error is displayed:
	
	  Query pooltags Failed c0000002
	
	CAUSE
	=====
	
	Poolmon.exe uses a global pooltag in the registry located at a value called
	GlobalFlag. The default value for GlobalFlag is 0, so Windows NT does not expend
	extra overhead in gathering pooltag information.
	
	RESOLUTION
	==========
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	To allow Windows NT to gather pooltag information, the GlobalFlag value must be
	changed using Registry Editor (Regedt32.exe). Before making changes, write down
	the current value of GlobalFlag so that it can be reset once running Poolmon.exe
	is no longer necessary.
	
	The following hex values for GlobalFlag will set up memory tagging in Windows NT
	for the following versions:
	
	Windows NT 3.5: 0x01000000
	Windows NT 3.51: 0x00000400
	Windows NT 4.0: 0x00000400
	
	If you are running Windows NT version 3.51 or 4.0 but do not have the Windows NT
	4.0 Resource Kit, follow these steps.
	
	To change the value of the GlobalFlag, you need to modify its value in the
	registry.
	
	1. Start Registry Editor (Regedt32.exe) and locate the following subkey:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control
	  \Session Manager
	
	2. Double-click on the GlobalFlag Value on the right pane.
	
	3. In the Data Type field, select REG_DWORD and click OK.
	
	4. In the Data Field, type in either 01000000 or 00000400, depending on the
	  version of Windows NT. Select the Hex option and click OK.
	
	     Range:   0 - 0xFFFFFFFF (not continuous)
	     Default: 0
	
	5. Quit Registry Editor, shutdown, and restart your computer.
	
	If you have a computer running Windows NT 4.0 and you have the resource kit,
	there is utility called GFLAGS. GFLAGS is a GUI tool that enables a developer or
	system administrator to edit the NtGlobalFlag settings for Windows NT Server or
	Windows NT Workstation without having to make manual changes in the registry.
	
	To use this utility to enable Pool tagging:
	
	1. Double-click on the Gflags.exe file in the resource kit directory or open a
	  MS-DOS command prompt and type in GFLAGS and press Enter.
	
	2. After the GFLAGS window opens, set the destination in the upper windows to
	  System Registry.
	
	3. In the lower portion of the window, click to select the "Enable Pool Tagging"
	  check box.
	
	4. The computer running Windows NT will have to be restarted for the change to
	  take affect.
	
	GFLAGS can also set the flag required for the kernel feature of Oh.exe, a tool
	that shows the handles of open windows. For usage information, at a MS- DOS
	command prompt type:
	
	  gflags /?
	
	MORE INFORMATION
	================
	
	GlobalFlag consists of 32 bits that are used as switches to enable or disable
	several different advanced internal system diagnostics and troubleshooting
	tests.
	
	
	NOTE: In Windows NT versions 3.51 and earlier, changing the value of this entry
	to 0x20100000 disabled the OS/2 subsystem and caused OS/2-bound applications to
	run in a virtual DOS computer. This does not work in Windows NT 4.0.
	======================================================================
	Keywords          : kbusage 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : WinNT:3.5,3.51,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
