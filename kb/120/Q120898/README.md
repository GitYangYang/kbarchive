---
layout: page
title: "Q120898: File Manager and Shell Report Total Size of CD-ROMs as 128 MB"
permalink: /kb/120/Q120898/
---

## Q120898: File Manager and Shell Report Total Size of CD-ROMs as 128 MB

{% raw %}

	Article: Q120898
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.x,4.x,5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	File Manager and the MS-DOS Shell may report 128 megabytes (MB) as the total
	size of a CD-ROM and zero (0) MB as the amount of free space. This occurs
	because the Microsoft CD-ROM Extensions (MSCDEX) reports 128 MB as the capacity
	of a CD regardless of the real capacity or true remaining free space on the CD.
	
	MORE INFORMATION
	================
	
	MSCDEX reports 128 MB for the MS-DOS DISK INFO function call. This MS-DOS API is
	used by File Manager and Shell. Although it is not difficult to find the
	capacity of a CD-ROM, MSCDEX does not use this information. MSCDEX reports a
	total of 65,535 clusters of 2 kilobytes each and 0 free clusters.
	
	Additional query words: 4.00 5.00 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a
	Version           : MS-DOS:3.x,4.x,5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
