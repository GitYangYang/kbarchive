---
layout: page
title: "Q71586: MS-DOS: Running CHKDSK As A Child Process"
permalink: /kb/071/Q71586/
---

## Q71586: MS-DOS: Running CHKDSK As A Child Process

{% raw %}

	Article: Q71586
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:2.x,3.x,4.x,5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 2.11, 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	To maintain a fixed disk, you may wish to run CHKDSK /F as a child process from
	an application that runs continuously. However, you should not do this.
	
	CHKDSK assumes that the file allocation table (FAT) is in a stable state. If
	CHKDSK detects an error and attempts to correct it by making changes to the FAT,
	CHKDSK could destroy the FAT operations that MS-DOS has done up to that point.
	
	More specifically, if CHKDSK is run when a file is open, the chain of clusters
	"owned" by the file could be altered in the FAT by CHKDSK. When the file is
	closed and MS-DOS finishes updating the FAT and the directory, you may be left
	with an error in the FAT.
	
	
	Additional query words: 6.22 2.11 3.00 3.20 3.21 3.30 3.30a 4.00 4.01 4.01a 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a kbMSDOS211
	Version           : MS-DOS:2.x,3.x,4.x,5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
