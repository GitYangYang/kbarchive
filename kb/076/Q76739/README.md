---
layout: page
title: "Q76739: Updating Backup Files with NMAKE &amp; ALL Target-Dependency"
permalink: /kb/076/Q76739/
---

## Q76739: Updating Backup Files with NMAKE &amp; ALL Target-Dependency

{% raw %}

	Article: Q76739
	Product(s): Microsoft Programming Utilities
	Version(s): 1.01,1.11,1.12,1.13,1.2,1.21,1.3,1.4
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft NMAKE Utility for MS-DOS, versions 1.01, 1.11, 1.12, 1.13, 1.2, 1.3, 1.4 
	- Microsoft NMAKE Utility for OS/2, versions 1.11, 1.12, 1.13, 1.21 
	- Microsoft NMAKE Utility for Windows NT 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The text below demonstrates using NMAKE and the ALL target-dependency (an NMAKE
	keyword) to copy or backup files that are out-of-date with respect to the
	previous copy or archive.
	
	MORE INFORMATION
	================
	
	The steps below create a .MAK file that copies the AUTOEXEC.BAT and CONFIG.SYS
	files to a directory named C:\BACKUP:
	
	1. Use a text editor to create COPY.MAK that contains the following text:
	
	     ALL: c:\backup\autoexec.bat c:\backup\config.sys
	
	     c:\backup\autoexec.bat: c:\autoexec.bat
	        copy c:\autoexec.bat c:\backup\autoexec.bat
	     c:\backup\config.sys: c:\config.sys
	        copy c:\config.sys c:\backup\config.sys
	
	  NOTE: The .MAK file above copies the AUTOEXEC.BAT files from the source
	  directory (C:\) to the target directory (C:\BACKUP). The files are copied
	  only if the files in the source directory have an older time/date stamp than
	  the files in the target directory.
	
	2. Create the C:\BACKUP directory if it does not already exist. To do so, type
	  the following at the MS-DOS command prompt:
	
	  " mkdir c:\backup" (without the quotation marks)
	
	3. To backup any changes you made to your AUTOEXEC.BAT or CONFIG.SYS files, type
	  the following at the MS-DOS command prompt:
	
	  " nmake /f copy.mak" (without the quotation marks)
	
	NMAKE processes only one dependency per makefile. If the makefile did not include
	the ALL target-dependency (an NMAKE keyword), only the first file would be
	copied and the second copy command would be ignored completely. The ALL target
	creates a dependency that depends on the completion of every task in the
	makefile. Without this statement, two dependencies are declared, only one of
	which would be processed.
	
	Page 645 of the "Microsoft Basic 7.0: Programmer's Guide" for versions 7.0 and
	7.1 presents a similar example. However, this example lacks the ALL
	target-dependency and does not work correctly as presented.
	
	Additional query words: kbinf 1.20 1.30 1.40 1.50 gp fault trap 13 lock
	
	======================================================================
	Keywords          :  
	Technology        : kbVCsearch kbAudDeveloper kbNMAKESearch kbNMAKE101DOS kbNMAKE111DOS kbNMAKE112DOS kbNMAKE113DOS kbNMAKE120DOS kbNMAKE130DOS kbNMAKE140DOS kbNMAKE111OS2 kbNMAKE112OS2 kbNMAKE113OS2 kbNMAKE121OS2
	Version           : :1.01,1.11,1.12,1.13,1.2,1.21,1.3,1.4
	
	=============================================================================
	

{% endraw %}
