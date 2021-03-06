---
layout: page
title: "Q237265: Encarta 2000: How Creation Dates Are Affected During Setup"
permalink: /kb/237/Q237265/
---

## Q237265: Encarta 2000: How Creation Dates Are Affected During Setup

{% raw %}

	Article: Q237265
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 
	Operating System(s): 
	Keyword(s): kbenv kbsetup kbimu
	Last Modified: 25-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Encarta Encyclopedia 2000 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how file creation dates are affected when you install
	Microsoft Encarta Encyclopedia 2000.
	
	MORE INFORMATION
	================
	
	When you install Encarta Encyclopedia 2000, certain files receive creation dates
	that are different from the creation dates for the same files on the Encarta
	Encyclopedia 2000 Installation and Resources Disc CD-ROM. When you install
	Encarta Encyclopedia 2000, the current date is assigned as the creation date for
	each of these files.
	
	NOTE: This unexpected behavior does not affect the performance of Encarta
	Encyclopedia 2000 or most other programs you run on your computer.
	
	To determine whether to skip or replace a file that is already installed on your
	computer, most Setup programs compare the version number of the installed file
	to the version number of the file to be installed. If the installed file is a
	later version or the same version as the file to be installed, Setup skips
	installing the file. If the installed file is an earlier version of the file to
	be installed, Setup replaces the installed file with the newer version.
	
	However, some Setup programs determine whether to skip or replace a matching file
	by comparing the creation date of the installed file to the creation date of the
	file to be installed. If the creation date of the installed file is the same as
	or later than the creation date of the file to be installed, Setup skips
	installing the file. If the creation date of the installed file is earlier than
	the creation date of the file to be installed, Setup replaces the installed
	file. You may experience problems with Setup programs that compare creation
	dates to determine if an installed file should be replaced.
	
	NOTE: Many Setup programs install .dll files that are shared by other programs.
	If you install a program that bases its installation of .dll files on creation
	dates, the program may not replace an older version of a .dll file installed on
	your computer with a newer version because the installed file has a later
	creation date than the newer version of the file. If you install a program that
	requires the latest .dll files under these conditions, you may be unable to run
	the program, or the program may not function properly.
	
	Additional query words: multi mult-media media mm ee2k
	
	======================================================================
	Keywords          : kbenv kbsetup kbimu 
	Technology        : kbHomeProdSearch kbHomeMMsearch kbEncartaSearch kbEncartaEncycSearch kbEncartaEnCyc2000
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
