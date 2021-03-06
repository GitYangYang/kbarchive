---
layout: page
title: "Q172086: FIX: Data Corruption with Row Buffering in Visual FoxPro 3.0"
permalink: /kb/172/Q172086/
---

## Q172086: FIX: Data Corruption with Row Buffering in Visual FoxPro 3.0

{% raw %}

	Article: Q172086
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b
	Operating System(s): 
	Keyword(s): kbcode kbvfp kbvfp300 kbvfp300b
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Using optimistic or pessimistic table buffering with multiple users trying to
	simultaneously update a table, located on a Windows 95 machine, certain records
	in the table may become corrupted. This is sometimes seen more often with
	optimistic row buffering. This behavior does not happen in Visual FoxPro 5.0 or
	5.0a.
	
	RESOLUTION
	==========
	
	Place the table(s) on a computer running Windows NT 4.0 using either the NT File
	System (NTFS) or File Allocation Table (FAT) hard disk partitions.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This has been corrected in Visual FoxPro 6.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	The example below uses a program to simulate 10 users opening the same table and
	simultaneously updating individual records.
	
	1. Create a table called ztest using the following command: CREATE TABLE ztest
	  (datadir c(100), inidir c(100), inifilenam c(12),; databasenm c(12), ihq_path
	  c(100), intrqlpath c(100))
	
	2. Add a record to the table using the following commands:
	
	        APPEND BLANK
	        REPLACE datadir WITH "First test record"
	
	3. Create two programs called Usera.prg and Userb.prg that contains the
	  following code:
	
	        LOCAL laAlias, lnX
	
	        SET EXCLUSIVE OFF
	        SET MULTILOCKS ON
	        SET REPROCESS TO 5
	
	        DIMENSION laAlias[10]
	        laAlias[1] = "A"
	        laAlias[2] = "B"
	        laAlias[3] = "C"
	        laAlias[4] = "D"
	        laAlias[5] = "E"
	        laAlias[6] = "F"
	        laAlias[7] = "G"
	        laAlias[8] = "H"
	        laAlias[9] = "I"
	        laAlias[10] = "J"
	
	        FOR lnX = 1 TO ALEN(laAlias)
	           USE ztest again ALIAS &laAlias[lnX] in 0 SHARED
	           SELECT &laAlias[lnX]
	           =CURSORSETPROP("BUFFERING",3)
	           APPEND BLANK
	        ENDFOR
	
	        FOR lnX = 1 TO ALEN(laAlias)
	           SELECT &laAlias[lnX]
	           REPLACE DataDir WITH STR(RECNO())+ "  UserA" + STR(RECCOUNT())
	           llError=TABLEUPDATE()
	           ?llERROR
	           IF !LLERROR
	              =MESSAGEBOX("Update Error",0,"Test")
	           ENDIF
	           USE
	        ENDFOR
	
	4. Place Ztest.dbf, Usera.prg, and Userb.prg in the same directory on a machine
	  running Windows 95.
	
	5. Share the folder and map the drive on another machine. This machine can be
	  running either a Windows 95 or Windows NT 4.0.
	
	6. Two users must work at the same time. One user will run Usera.prg on one
	  machine and one user will run Userb.prg on another machine.
	
	7. Both users run their programs from their respective Command windows
	  simultaneously. For best results, run the programs two or three times. The
	  corruption does not always show up on the first run.
	
	8. When the programs finish, look at the Ztest.dbf. Notice some of the records
	  contain corrupted data.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbvfp kbvfp300 kbvfp300b 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b
	Version           : WINDOWS:3.0,3.0b
	Issue type        : kbbug kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
