---
layout: page
title: "Q96557: MSAV Detects a Boot-Sector Virus but Fails to Clean It"
permalink: /kb/096/Q96557/
---

## Q96557: MSAV Detects a Boot-Sector Virus but Fails to Clean It

{% raw %}

	Article: Q96557
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	
	Microsoft Anti-Virus may detect a boot-sector virus (such as STONED or
	Michelangelo) but fail to clean it. This problem can be caused by either of the
	following conditions:
	
	- The boot-sector virus is on your DoubleSpace-compressed drive and your host
	  drive.
	
	- All the virus code is not being overwritten.
	
	MORE INFORMATION
	================
	
	The Boot-Sector Virus Is on Your DoubleSpace-Compressed
	
	Drive and Your Host Drive
	-------------------------
	
	Boot-sector viruses "infect" a drive by replacing the startup (boot) code that is
	stored at the beginning of the drive. A boot-sector virus is activated when you
	start your computer from the infected drive (usually drive C). Because the
	startup code on a DoubleSpace-compressed drive is never run, it is not possible
	for a boot-sector virus on a compressed drive to become activated. However, if a
	boot-sector virus is detected on a compressed drive, it is likely that the host
	drive is also infected.
	
	You can detect and clean viruses from all local drives by using the following
	command:
	
	  msav /c /l
	
	The /C switch causes Microsoft Anti-Virus to scan and clean the disk. The /L
	switch causes Microsoft Anti-Virus to scan all local drives except A and B.
	
	All Virus Code Is Not Being Overwritten
	---------------------------------------
	
	When a boot-sector virus infects a hard disk, it moves the original boot- sector
	information to another location on the disk and replaces it with virus code.
	Microsoft Anti-Virus finds the original boot-sector information and uses it to
	overwrite the virus code. If the original boot-sector information is incomplete
	or has been damaged in some way, some of the virus code may not be overwritten.
	When Microsoft Anti-Virus scans the drive and finds the remnant of the virus
	code, it reports it as a virus.
	
	Workaround If CHKDSK Reports 655,360 Total Bytes Memory
	-------------------------------------------------------
	
	If the Total Bytes Memory reported by MS-DOS CHKDSK is 655,360 bytes, the virus
	is not active, and the following steps should be taken to clean the remnant of
	the virus code from the drive:
	
	1. Back up all data on all partitions on the hard disk drive. You may want to
	  use the Microsoft Backup Compare feature to ensure that all files have been
	  backed up successfully.
	
	2. If the infected hard disk drive was partitioned with MS-DOS Fdisk, the virus
	  remnant can be cleaned by running MS-DOS Setup with the /M parameter. This
	  refreshes the master boot record (MBR) and overwrites any remaining virus
	  code.
	
	  To prevent the virus from infecting your MS-DOS disks, ensure they are write
	  protected before running MS-DOS Setup. To prevent your Uninstall disk from
	  becoming infected with the virus, turn off your computer and then start it
	  from a floppy disk known to be free of viruses before running MS-DOS Setup.
	
	3. Run Microsoft Anti-Virus to determine whether the procedure eliminated the
	  remaining virus code.
	
	Workaround If CHKDSK Reports Less Than 655,360 Total Bytes Memory
	-----------------------------------------------------------------
	
	If CHKDSK reports less than 655,360 total bytes memory, the virus may still be
	active. In this case, use the following steps:
	
	1. Boot from a write-protected system disk that is known to be free of virus
	  infection (such as your original MS-DOS 6 Upgrade Setup Disk 1).
	
	  NOTE: Although the 1.2-megabyte (MB) 5.25-inch floppy disks are write
	  protected, the 1.44 MB 3.5-inch floppy disks are not. If you have the 1.44-MB
	  floppy disks, slide the write-protect tab so that the write- protect slot is
	  open on all your disks. Scan the floppy disks to ensure they are not
	  infected. If they are, order new disks from Microsoft Sales Information
	  Center (MSIC) at (800) 426-9400.
	
	2. Insert Disk 3 of either the 1.2-MB or 1.44-MB disk set in drive A.
	
	3. Change to the MS-DOS command prompt at drive A and run Microsoft Anti-Virus.
	  For example, type the following at the MS-DOS command prompt, pressing ENTER
	  after each line:
	
	  " a:
	  msav c: /c /l" (without the quotation marks)
	
	4. Remove the floppy disk from drive A and restart your computer.
	
	5. Scan all hard disk drives to ensure the virus has been removed.
	
	NOTE: The new location of the original boot sector information may be different
	for each boot sector virus. Microsoft Anti-Virus can therefore clean only the
	boot sector viruses on the Microsoft Anti-Virus virus list.
	
	Which Boot Sector Is Executed During Startup?
	---------------------------------------------
	
	If drive C is uncompressed, its boot sector is run during system startup.
	If drive C is compressed, the boot sector of its host drive is run.
	
	What the Boot Sector Does
	-------------------------
	
	The boot-sector startup code in MS-DOS versions 5.0 and later does the
	following:
	
	- Confirms that the system files (IO.SYS and MSDOS.SYS) are the first two files
	  in the root directory of the drive.
	
	- Loads and executes the first three sectors of the IO.SYS file.
	
	The boot sector is executed by the master boot record (MBR). If you have more
	than one partition, the MBR determines which one to run using the partition
	table.
	
	How Boot-Sector Viruses Get on a Compressed Volume File (CVF)
	-------------------------------------------------------------
	
	If a drive is infected before you install DoubleSpace, some boot-virus
	information may be replicated on the DoubleSpace CVF. Although it cannot affect
	the system from the DoubleSpace volume, the signatures may still be detected
	here. To correct this, clean both the host drive and DoubleSpace- compressed
	drive.
	
	Additional query words: 6.00 6.20 change "setup /m" double space MWAV MSAV dblspace
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
