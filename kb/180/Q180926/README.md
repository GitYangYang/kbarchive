---
layout: page
title: "Q180926: Setting Registry Quota Before the Reboot of Unattended Install"
permalink: /kb/180/Q180926/
---

## Q180926: Setting Registry Quota Before the Reboot of Unattended Install

{% raw %}

	Article: Q180926
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbOPK kbSBK
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	During an unattended installation of Windows NT 4.0 when using Sysdiff to
	install additional software, the following error may occur:
	
	  System Process - Low on Registry Quota
	  Your system is running low on registry quota. Start the System option in
	  the Control Panel and choose the Virtual Memory button to increase the
	  registry quota.
	
	
	Because the error occurs after the first reboot during unattended installation,
	there is no way to access the System tool in Control Panel to change the
	registry quota size.
	
	RESOLUTION
	==========
	
	To resolve this problem, and allow setup to complete while using unattended
	installation, follow these steps:
	
	1. From the I386 installation folder, expand the SYSTEM._ file and call it
	  System. Place it in any directory on the hard drive.
	
	  NOTE: Depending on which product you are installing (that is, Enterprise
	  Server, Windows NT Server, Small Business Server) the System file may not be
	  compressed, in which case it is not necessary to use the EXPAND command to
	  uncompress the file.
	
	2. Run Registry Editor (Regedt32.exe).
	
	  WARNING: Using Registry Editor incorrectly can cause serious problems that may
	  require you to reinstall your operating system. Microsoft cannot guarantee
	  that problems resulting from the incorrect use of Registry Editor can be
	  solved. Use Registry Editor at your own risk.
	
	  For information about how to edit the registry, view the "Changing Keys And
	  Values" online Help topic in Registry Editor (Regedit.exe) or the "Add and
	  Delete Information in the Registry" and "Edit Registry Data" online Help
	  topics in Regedt32.exe. Note that you should back up the registry before you
	  edit it.
	
	3. Go to the HKey_Local_Machine key, and then from the Registry menu, click Load
	  Hive.
	
	4. Open the System hive from the directory copied to in Step 1.
	
	5. When prompted, give the System hive a unique Key Name. (that is, a name other
	  than an existing hive name, such as Test).
	
	6. Expand the loaded System file (that is, Test) and select the
	  ControlSet001\Control key.
	
	7. From the Edit menu, click Add Value and type the following:
	
	  Value Name: RegistrySizeLimit
	  Data Type : REG_DWORD
	  Data      : <the size you would normally put in via Control Panel>
	
	  NOTE: Remember that through Control Panel the option is displayed in decimal
	  form. Ensure that you select the correct Radix to match the number you
	  specify, and then select OK.
	
	8. Select the loaded System key (that is, Test), and then, from the Registry
	  menu, click Unload Hive.
	
	  NOTE: This exports the System hive back to the location you saved it in
	  originally in Step 1.
	
	9. Exit Registry Editor.
	
	10. Rename the System hive back to "System._" (only if the System hive was
	  compressed to begin with), without the quotation marks.
	
	11. Copy the System._ (or System) file back in the I386 installation folder.
	
	12. Rerun the installation.
	
	Additional query words: registry alter additional unattended setup install
	
	======================================================================
	Keywords          : kbOPK kbSBK 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
