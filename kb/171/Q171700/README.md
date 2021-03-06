---
layout: page
title: "Q171700: Error Message: Billadd.dll Is Linked to Missing Export Mcm.dll"
permalink: /kb/171/Q171700/
---

## Q171700: Error Message: Billadd.dll Is Linked to Missing Export Mcm.dll

{% raw %}

	Article: Q171700
	Product(s): The Microsoft Network
	Version(s): WINDOWS:2.0
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup
	Last Modified: 13-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to connect to MSN, The Microsoft Network, after you install MSN
	2.0, you may receive the following error message:
	
	  Billadd.dll is linked to missing export Mcm.dll.
	
	CAUSE
	=====
	
	The Billadd.dll file in the Program Files\The Microsoft Network folder and the
	Mcm.dll file in the Windows\System folder may be mismatched.
	
	RESOLUTION
	==========
	
	To resolve this issue, delete each copy of the Mcm.dll file from your hard
	drive, and then extract a new copy of the Mcm.dll file from your original
	Windows 95 disks or CD-ROM to the Windows\System folder. To do so, use the
	following steps:
	
	1. Click Start, point to Find, and then click Files Or Folders.
	
	2. In the Named box, type "mcm.dll" (without the quotation marks), and then
	  click Find Now.
	
	3. In the list of found files, right-click each Mcm.dll file, and then click
	  Delete. Continue until the list of found files is empty.
	
	4. Close the Find: Files Named Mcm.dll window.
	
	5. Extract a new copy of the Mcm.dll file from your original Windows 95 disks or
	  CD-ROM to the Windows\System folder.
	
	The Mcm.dll file is located in the Win95_07.cab cabinet file on the Windows 95
	CD-ROM, in the Win95_10.cab cabinet file on the Windows 95 OEM Service Release 2
	CD-ROM, in the Win95_07.cab cabinet file on disk 7 of the Windows 95 DMF format
	disks, and in the Win95_11.cab cabinet file on disk 11 of the Windows 95 non-DMF
	format disks.
	
	For information about using the Extract tool, type "extract" (without the
	quotation marks) at a command prompt, or see the following article in the
	Microsoft Knowledge Base:
	
	  Q129605 How to Extract Original Compressed Windows Files
	
	MORE INFORMATION
	================
	
	If extracting a new copy of the Mcm.dll file does not resolve the issue, use the
	following steps:
	
	1. Click Start, point to Find, and then click Files Or Folders.
	
	2. In the Named box, type "billadd.dll" (without the quotation marks), and then
	  click Find Now.
	
	3. In the list of found files, right-click each Billadd.dll file, and then click
	  Delete. Continue until the list of found files is empty.
	
	4. Close the Find: Files Named Billadd.dll window.
	
	5. Insert the MSN 2.0 CD-ROM into the CD-ROM drive. When the Welcome To MSN
	  screen appears, follow the instructions on the screen to reinstall MSN. If
	  the Welcome To MSN screen does not appear, follow these steps:
	  a. Double-click My Computer.
	
	  b. Right-click the MSN (CD-ROM drive) icon, and then click Explore.
	
	  c. Double-click the Msnstart.exe file.
	
	Additional query words: msnet msnetwork microsoft-net m.s.n.
	
	======================================================================
	Keywords          : kberrmsg kbsetup 
	Technology        : kbMSNSearch kbMSN200
	Version           : WINDOWS:2.0
	
	=============================================================================
	

{% endraw %}
