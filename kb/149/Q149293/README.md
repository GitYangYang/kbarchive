---
layout: page
title: "Q149293: File Manager Can't View Permissions After NWCONV.EXE Is Run"
permalink: /kb/149/Q149293/
---

## Q149293: File Manager Can't View Permissions After NWCONV.EXE Is Run

{% raw %}

	Article: Q149293
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5,3.51
	Operating System(s): 
	Keyword(s): kbtool
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	You create a subdirectory on the NetWare server, assign a user to the
	subdirectory, and then revoke all permissions to the user. When you run
	Nwconv.exe, you are unable to view the permissions on any subdirectory below
	\APPS in File Manager, security, permissions on the subdirectory or any
	subdirectory below that. You will receive the following error message when you
	try to view the permissions:
	
	  The security information for (directory path) are not standard and cannot be
	  displayed. Do you want to overwrite the current security information?
	
	Example
	-------
	
	On a NetWare server:
	
	SYSVOL
	  \APPS USER [           ] Assign no permissions assigned.
	     \A
	     \B
	
	On the Windows NT server, after you run Nwconv.exe:
	
	SYSVOL
	   \APPS      No permissions have been assigned to the subdirectories
	     \A       below APPS including groups that should have permissions
	     \B       assigned.
	
	CAUSE
	=====
	
	During the conversion, an ACE (access control entry) was added for the user with
	no permissions, but not all of the NTFS attributes were correctly added to the
	file. Therefore File Manager is unable to view the permission on the
	subdirectories.
	
	RESOLUTION
	==========
	
	Nwconv.exe code no longer adds an ACE to the ACL (access control list) for a
	user that does not have any permissions assigned to subdirectories.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. This
	problem was corrected in the latest Windows NT 3.51 U.S. Service Pack. For
	information on obtaining the Service Pack, query on the following word in the
	Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbtool 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : winnt:3.5,3.51
	
	=============================================================================
	

{% endraw %}
