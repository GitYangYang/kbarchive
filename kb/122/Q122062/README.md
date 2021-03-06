---
layout: page
title: "Q122062: Err Msg: This Version of Mail Is Too Old..."
permalink: /kb/122/Q122062/
---

## Q122062: Err Msg: This Version of Mail Is Too Old...

{% raw %}

	Article: Q122062
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 31-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you install version 3.0 or later of the retail version of Microsoft Mail
	or the version of Microsoft Mail that ships with Windows for Workgroups version
	3.11 over the older version of Mail shipped with Windows for Workgroups 3.1, you
	receive the following error message:
	
	  This version of Mail is too old to access your message file.
	
	NOTE: Choosing OK closes Mail.
	
	CAUSE
	=====
	
	NOTE: This information applies to both Microsoft DoubleSpace and Microsoft
	DriveSpace. For MS-DOS 6.22, use DRVSPACE in place of DBLSPACE for commands and
	filenames.
	
	In Windows for Workgroups version 3.11, you can use two different types of
	compression on the Mail message file (.MMF): DoubleSpace Security or Highest
	Security. The difference between these is the encryption method employed. The
	DoubleSpace option is less heavily encrypted and allows DoubleSpace to compress
	the file on a DoubleSpace volume.
	
	The aforementioned error message can occur when you are using Windows for
	Workgroups version 3.11 if DoubleSpace Security is enabled rather than Highest
	Security. Windows for Workgroups Mail 3.1 and the retail version of Microsoft
	Mail cannot read the Windows for Workgroups 3.11 .MMF because they cannot read
	the DoubleSpace encryption method.
	
	To use Windows for Workgroups Mail version 3.1 or the retail version of Microsoft
	Mail, you must use the Highest Security method.
	
	RESOLUTION
	==========
	
	To change the encryption method, do the following:
	
	1. Rename the current MSMAIL.EXE to MSMAIL.SAV. This file is usually found in
	  the Windows directory although it is possible for it to be located in another
	  directory.
	
	2. Expand the file MSMAIL.EX_ from your original Windows for Workgroups version
	  3.11 disks. At an MS-DOS command prompt, change to your Windows directory,
	  and type the following command
	
	  expand <drive>:\msmail.ex_ <destination>:\windows\msmail.exe
	
	  where <drive> is the floppy disk drive containing your original Windows
	  for Workgroups disk and <destination> is the drive containing Windows.
	
	  NOTE: This file is located on Disk 2 of the 1.2-MB 5.25-inch disk set and Disk
	  3 of the 1.44-MB 3.5-inch disk set.
	
	3. Start MSMAIL.EXE from the Windows directory.
	
	4. From the Mail menu, choose Options. Change DoubleSpace Security to Highest
	  Security.
	
	5. From the File menu, choose Exit And Sign Out.
	
	6. Delete the MSMAIL.EXE file that you expanded in step 2--it is no longer
	  required.
	
	7. Rename the saved copy of the mail executable MSMAIL.SAV to MSMAIL.EXE.
	
	8. Restart Mail.
	
	If the compression options listed are missing, check to see if the MSMAIL.EXE
	file being used was in the Windows directory. If MSMAIL.EXE was being called
	from a different location, run Mail from the Windows directory and repeat the
	above steps.
	
	NOTE: The physical size of the .MMF does not change as a result of changing the
	encryption method; however, a progress bar is displayed at the bottom of the
	Mail screen during the conversion process. This conversion process takes
	approximately 10 to 15 seconds per megabyte of .MMF size.
	
	If Microsoft Mail cannot convert the .MMF to Highest Security but still functions
	when you are using Windows for Workgroups version 3.11, proceed as follows:
	
	1. Run Microsoft Mail, and choose Export Folder from the File menu.
	
	2. Export all folders to another file (for example, EXPORT.MMF).
	
	3. Rename the MSMAIL.MMF file to MSMAIL.OLD.
	
	4. Run the retail version of Microsoft Mail or Windows for Workgroups version
	  3.10 Mail.
	
	5. When prompted for the location of the .MMF, select the exported file (for
	  example, EXPORT.MMF).
	
	  A message informing you that this is a backup message file should appear.
	  Choose OK to convert this exported .MMF to the active .MMF for Mail.
	
	6. Mail should then function normally.
	
	Additional query words: error message err msg
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311
	Version           : WINDOWS:3.11
	
	=============================================================================
	

{% endraw %}
