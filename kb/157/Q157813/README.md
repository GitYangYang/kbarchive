---
layout: page
title: "Q157813: FIX: Branch or Rollback of Shared File May Cause Corruption"
permalink: /kb/157/Q157813/
---

## Q157813: FIX: Branch or Rollback of Shared File May Cause Corruption

{% raw %}

	Article: Q157813
	Product(s): Microsoft SourceSafe
	Version(s): WIN95
	Operating System(s): 
	Keyword(s): kbSSafe400bug kbSSafe500fix
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe, 16-bit, for Windows, version 4.0 
	- Microsoft Visual SourceSafe, 32-bit, for Windows 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you Branch or Rollback a shared file that uses Keyword Expansion, previous
	versions of that file may become corrupt. The corruption will be seen in all
	versions two or more behind the current version of the file. For example, if you
	have a shared file that uses Keyword Expansion that contains 10 versions and you
	Rollback that file to version 8, versions 1 through 5 may be corrupted.
	
	CAUSE
	=====
	
	This problem occurs when a Branch is executed on a file that uses Keyword
	Expansion. When you Rollback a shared file, Visual SourceSafe actually performs
	a branch in conjunction with the Rollback. It is this Branch that results in the
	problem, not the Rollback itself.
	
	RESOLUTION
	==========
	
	Do not use Keyword Expansion or do not Rollback a file that uses Keyword
	Expansion in versions prior to 4.0.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Visual SourceSafe version 4.0
	and 4.0a for Windows. This problem was corrected Visual SourceSafe for Windows,
	version 5.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Use an ASCII text editor, such as Notepad, to create a new text file.
	
	2. Add the following text to the beginning of line 1:
	
	        $History:: $
	
	3. Add the following text to the beginning of line 2:
	
	        This is my entry for version 2
	
	4. Save the file and add it to a Visual SourceSafe project.
	
	5. Share the file with another Visual SourceSafe project or subproject.
	
	6. Check out the file from Visual SourceSafe.
	
	7. Add a new line to the checked out file that reads:
	
	        This is my entry for version 3
	
	8. Save the changes and check the file back into Visual SourceSafe.
	
	9. Repeat steps 6 through 8 until you have added a total of 6 versions of
	  comments in the file.
	
	10. Branch off the shared copy of the file.
	
	11. Right-click on the branched copy of the file, and then choose Show History.
	
	12. Do a View on any version two or more versions behind the branched version.
	  For example, if version 6 is the branched version, note that version 4 or
	  earlier of the file has missing data.
	
	NOTE: The problem would also occur if you were to replace step 10 above with a
	Rollback because Visual SourceSafe would perform a Branch at this point.
	
	REFERENCES
	==========
	
	For more information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q157082 BUG: Rollback of a Shared Files Rolls to Unexpected Version
	
	  Q156717 PRB: Rollback of Shared Files Forces a Branch
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400bug kbSSafe500fix 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe400 kbSSafe16bitSearch kbSSafe32bitSearch
	Version           : WIN95
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
