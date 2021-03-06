---
layout: page
title: "Q192494: SMS: Netspeed.dat File Is Compressible"
permalink: /kb/192/Q192494/
---

## Q192494: SMS: Netspeed.dat File Is Compressible

{% raw %}

	Article: Q192494
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbtshoot smsremtshoot kbRemoteProg
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	If you configure your Systems Management Server site settings to prevent clients
	from taking inventory over a slow link, inventory may still be taken if your
	modem has compression enabled.
	
	CAUSE
	=====
	
	When you take inventory, Netspeed.com attempts to determine the link speed by
	reading the file Netspeed.dat across the client connection. A total of 3,400
	bytes are read from Netspeed.dat on the logon server. The speed is measured in
	the number of milliseconds to read the total bytes. The default of 3,400 bytes
	within 850 milliseconds indicates a fast link. If it takes 850 milliseconds or
	longer, it is considered a slow link.
	
	WORKAROUND
	==========
	
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
	
	You may adjust the default 850 millisecond threshold by modifying a registry
	key.
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate the Slow Net Threshold Speed value under the following key in the
	  registry:
	
	     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Systems Management Server
	     \Components\SMS_Maintenance_Manager\Slow Net Threshold Speed
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	3. On the Edit menu, click DWORD, type a value appropriate for your
	  configuration, and then click OK.
	
	4. Quit Registry Editor.
	
	For additional information about this registry value, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q131011 SMS: Netspeed.com Internals
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2.
	
	MORE INFORMATION
	================
	
	When Netspeed.com reads Netspeed.dat over a RAS connection using modem
	compression, the contents of the Netspeed.dat file may be compressed to a
	smaller size, allowing Netspeed.com to misinterpret the speed of the RAS link.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q142267 SMS: Netspeed Returns False Speed Over Compression-Capable Link
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbtshoot smsremtshoot kbRemoteProg 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
