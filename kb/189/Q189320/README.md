---
layout: page
title: "Q189320: Persistent Dial on Demand Connection Fails After 20 Minutes"
permalink: /kb/189/Q189320/
---

## Q189320: Persistent Dial on Demand Connection Fails After 20 Minutes

{% raw %}

	Article: Q189320
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Routing and Remote Access Service Update for Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	When you attempt to establish a permanent connection between a system running
	Routing and Remote Access Service and another router using a dial on demand
	connection, the modem disconnects after 20 minutes of inactivity. This
	disconnection is regardless of enabling the Persistent Connection radio button
	on the Dialing tab when you configure the dial on demand interface.
	
	CAUSE
	=====
	
	This problem is because a registry setting is overriding the Persistent
	Connection option.
	
	RESOLUTION
	==========
	
	To work around this problem, it will be necessary to modify the autodisconnect
	time in the registry.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it. If
	you are running Windows NT, you should also update your Emergency Repair Disk
	(ERD).
	
	The AutoDisconnect value is located in:
	
	HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\RemoteAccess
	\Parameters
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	Value: AutoDisconnect
	Data Type: REG_DWORD
	Default Value: 14
	Value Range: 0-6000
	
	This value sets the time interval (in minutes/converted to hex), after which
	inactive connections are terminated. Inactivity is measured by lack of session
	data transfer.
	
	To ensure that a Persistent Connection does not disconnect because of inactivity
	over the line, you will need to set the above parameter to 0, especially if
	clients are running NetBIOS datagram applications. Setting this parameter to 0
	disables AutoDisconnect. The default entry is 14h (20 in decimal). The valid
	range for this entry can be from 0-6000 (24,576 minutes). If you do want to set
	a specific time period for the disconnect feature, you will need to convert the
	number of minutes (before inactivity disconnect) to hex and insert this number
	in the registry value detailed above.
	
	Additional query words: DOD persistent routing autodisconnect idle
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbRRASNTSearch kbRRASNT400
	Version           : WinNT:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
