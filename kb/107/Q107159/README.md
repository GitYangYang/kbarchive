---
layout: page
title: "Q107159: MS-DOS 6.2 Stacker Conversion CONVERT.TXT File"
permalink: /kb/107/Q107159/
---

## Q107159: MS-DOS 6.2 Stacker Conversion CONVERT.TXT File

{% raw %}

	Article: Q107159
	Product(s): Microsoft Disk Operating System
	Version(s): 6.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 6.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains the "MS-DOS 6.2 Conversion Disk for Users of Stacker"
	CONVERT.TXT file.
	
	MORE INFORMATION
	================
	
	CONVERT.TXT
	-----------
	
	This file provides instructions and information about converting your Stacker
	disk-compression software to DoubleSpace. This file contains the following
	topics:
	
	1. Converting Stacker disk-compression software to DoubleSpace
	
	2. Using Stacker floppy disks with DoubleSpace
	
	3. Free-space requirements for converting a Stacker drive
	
	4. DoubleSpace could not convert a Stacker drive because there was not enough
	  free space
	
	5. DoubleSpace cannot convert a Stacker drive because there is not enough free
	  memory
	
	6. You have less compressed disk space with DoubleSpace than with Stacker
	
	7. After converting your Stacker drives to DoubleSpace, your network does not
	  work
	
	8. The conversion program cannot continue because there is not enough
	  environment space
	
	9. Converting your Stacker drives if you use 4DOS or NDOS
	
	10. DoubleSpace cannot convert a Stacker 3.1 volume
	
	1. Converting Stacker Disk-Compression Software to DoubleSpace
	--------------------------------------------------------------
	
	To convert your Stacker disk-compression software to DoubleSpace, carry out the
	following procedure.
	
	NOTE: To convert a Stacker floppy disk to DoubleSpace format, see Section 2
	below.
	
	NOTE: If your version of Stacker is 1.1 or 3.1, or if you compressed your drive
	with a cluster size other than 8K, you cannot automatically convert your Stacker
	drive; you must convert it manually, as described in the README.TXT file in the
	directory that contains your MS-DOS files.
	
	1. Insert the Stacker Conversion Disk in drive A or B.
	
	2. Change to your floppy disk drive. For example, type "A:" (without the
	  quotation marks) or "B:" (without the quotation marks) at the command prompt.
	
	3. Type "CONVERT" (without the quotation marks) at the command prompt.
	
	  Follow the instructions on your screen. DoubleSpace will update the first
	  version of the DBLSPACE.EXE and DBLSPACE.HLP files in your path.
	
	  NOTE: If you have other versions of the DBLSPACE.EXE and DBLSPACE.HLP files on
	  your computer, cancel the Setup program and update these versions manually by
	  copying these files from the Stacker conversion disk to your hard disk. Then
	  run the CONVERT program again.
	
	  When DoubleSpace restarts your computer, make sure to remove disks from all
	  floppy disk drives.
	
	2. Using Stacker Floppy Disks with DoubleSpace
	----------------------------------------------
	
	If you have floppy disks that were compressed by using Stacker, you must convert
	them to DoubleSpace format in order to use them with DoubleSpace.
	
	When DoubleSpace Setup converts your Stacker drives to DoubleSpace format, it
	also converts any compressed floppy disks or other removable media that are
	currently mounted. After you have completed DoubleSpace Setup, you can convert
	other floppy disks and removable media from Stacker to DoubleSpace format by
	using the Convert Stacker command.
	
	If a compressed floppy disk contains at least .9 MB of free space, you can
	convert it to DoubleSpace format by choosing the Convert Stacker option from the
	Tools menu in DoubleSpace, or by typing DBLSPACE /CONVSTAC at the MS-DOS command
	prompt.
	
	If a floppy disk contains less than .9 MB of free space, you can convert it to
	DoubleSpace format manually by carrying out the following procedure:
	
	1. Insert the floppy disk in drive A or B.
	
	2. Move the STACVOL.DSK file to the host drive on your hard disk. To determine
	  which drive is your host drive, type DBLSPACE /LIST at the command prompt.
	  The host drive is listed under the CVF Filename column. For example, if
	  D:\DBLSPACE.000 is the CVF Filename associated with drive C, drive D is the
	  host drive.
	
	  When you move the file, change its extension to .001. For example if the
	  floppy disk is in drive A, and your host drive is drive D, type the following
	  at the command prompt:
	
	  " move a:\stacvol.dsk d:\stacvol.001" (without the quotation marks)
	
	  If there is insufficient disk space, start DoubleSpace by typing DBLSPACE at
	  the command prompt, and then choose Change Size from the Drive menu. Make the
	  size of the uncompressed drive large enough to contain the Stacker compressed
	  volume file.
	
	3. Delete unnecessary Stacker files from the floppy disk. For example, if you
	  have Stacker 2.0, delete STACKER.DRV. If you have Stacker 3.0, delete
	  STACKER.EXE and README.STC. (Use the ATTRIB -R README.STC command before
	  deleting the file to remove its read-only attribute.)
	
	4. Covert the compressed volume file to DoubleSpace format, as in the following
	  example:
	
	  dblspace /convstac=d:\stacvol.001
	
	  After DoubleSpace converts the file, it will mount it.
	
	5. Make sure your floppy disk is in drive A or B, and then compress it by
	  choosing the Existing Drive command from the Compress menu in DoubleSpace.
	  Follow the instructions on your screen.
	
	  DoubleSpace mounts the floppy drive after it finishes compressing the floppy
	  disk.
	
	6. Quit DoubleSpace.
	
	7. Use the DIR /A:H and DIR /A:S commands to determine whether you have any
	  hidden or system files and directories on the new compressed drive (the drive
	  created in step 4). If you have any hidden or system files and directories,
	  use the ATTRIB -S -H command to remove their attributes. For more information
	  about using the DIR and ATTRIB commands, see MS-DOS Help.
	
	  NOTE: If you have any hidden or system directories, make sure to check whether
	  those directories contain any hidden or system files and subdirectories.
	
	8. Use the XCOPY command to copy all the files on the new compressed drive (the
	  drive created in step 4) on your hard disk to the compressed floppy disk. For
	  example, if the compressed drive is J and the floppy disk is in drive A, type
	  the following at the command prompt:
	
	  " xcopy j:\*.* a: /s" (without the quotation marks)
	
	9. Delete the compressed drive from your hard disk. For example, if the
	  compressed drive is J, type the following at the command prompt:
	
	  " dblspace /delete j:" (without the quotation marks)
	
	  To confirm the deletion, type Y.
	
	10. If you removed the attributes of any files and directories in step 7, use
	  the ATTRIB +H and ATTRIB +S commands to restore those attributes to the
	  files and directories on the floppy disk.
	
	3. Free-Space Requirements for Converting a Stacker Drive
	---------------------------------------------------------
	
	To convert a Stacker drive to DoubleSpace format, the drive must contain some
	free space. To convert your startup hard disk, the drive must contain at least
	1.7 MB of free space. To convert other hard drives and floppy disks, the drive
	or disk must contain at least 1.0 MB of free space.
	
	1. DoubleSpace Could Not Convert a Stacker Drive Because There Was Not Enough
	  Free Space
	
	DoubleSpace indicates how much free space needs to be free on your startup or
	uncompressed drive. Make a note of this amount. Then carry out the following
	procedure:
	
	1. Type the following at the command prompt:
	
	  " chkdsk drive:" (without the quotation marks)
	
	  For the drive: parameter, type the drive letter of your uncompressed drive
	  followed by a colon (:). A line similar to the following should appear on
	  your screen:
	
	  20386 bytes available on disk
	
	2. Delete unnecessary files or move files to another drive until you have enough
	  free disk space. You might want to back up the files before you delete them.
	
	  IMPORTANT Do not delete your COMMAND.COM, AUTOEXEC.BAT, or CONFIG.SYS files,
	  your hidden Stacker or system files, or the STACKER.COM and SSWAP.COM files
	  in your Stacker directory. If you cannot delete enough unnecessary files, use
	  the SDEFRAG /G command to make more uncompressed space available, or contact
	  your disk-compression software vendor.
	
	3. Run DoubleSpace again.
	
	4. 
	
	  DoubleSpace Cannot Convert a Stacker Drive Because There is Not Enough Free
	  Memory
	
	If DoubleSpace displays a message that it cannot convert Stacker because there is
	not enough free memory, carry out the procedures in "An MS-DOS-based program
	displays an out-of-memory message" in the chapter "Diagnosing and Solving
	Problems" of the Microsoft MS-DOS 6 User's Guide.
	
	IMPORTANT: When carrying out procedure 2 from the User's Guide, do not bypass any
	commands that enable access to your Stacker drives. For example, don't bypass
	the DEVICE commands that load the STACKER.COM and SSWAP.COM commands.
	
	1. You Have Less Compressed Disk Space with DoubleSpace Than With Stacker
	
	If you convert a drive from Stacker to DoubleSpace, DoubleSpace might show that
	you have less compressed disk space than you had with Stacker. However, because
	DoubleSpace is thoroughly integrated with the MS-DOS operating system, it
	estimates compressed disk space more accurately than Stacker does. In fact, you
	may actually have more compressed disk space than you had with Stacker,
	regardless of what Stacker showed.
	
	Also, unlike Stacker, DoubleSpace continually updates its compressed disk space
	estimates. So, as you work with a compressed drive, DoubleSpace updates its
	estimates to reflect the actual current state of file compression on your
	drive.
	
	1. After Converting Your Stacker Drives to DoubleSpace, Your Network Does Not
	  Work
	
	If your network files were located on your uncompressed drive before you
	converted your drives to DoubleSpace, your network will probably not work after
	conversion. To solve this problem, copy your network files from your
	uncompressed (local) drive to your compressed drive. (To determine which drives
	are local and compressed, use the DBLSPACE /LIST command.) Make sure the network
	files have the same path as the network commands in your CONFIG.SYS file.
	
	1. The Conversion Program Cannot Continue Because There is Not Enough
	  Environment Space
	
	If the MS-DOS Stacker conversion program cannot continue because there is not
	enough environment space, you need to temporarily increase your environment
	space. To do this, carry out the following procedure.
	
	1. Examine the contents of your CONFIG.SYS file. If the file contains a SHELL
	  command that includes the /E switch, note the number specified by the /E
	  switch. This is your current environment space.
	
	  If your CONFIG.SYS file does not contain a SHELL command, or if the SHELL
	  command does not contain a /E switch, your current environment space is 256
	  bytes.
	
	2. At the command prompt, type the COMMAND command followed by the /E switch and
	  a number equal to your current environment space plus at least 100 bytes. For
	  example, if your environment space is currently 512 bytes, type the following
	  at the command prompt:
	
	  " command /e:612" (without the quotation marks)
	
	3. To convert your Stacker disk-compression software to DoubleSpace, carry out
	  the procedure in section 1 of this file.
	
	9. Converting Your Stacker Drives If You Use 4DOS or NDOS
	---------------------------------------------------------
	
	If you use the 4DOS or NDOS command interpreter, carry out the following
	procedure to convert your Stacker drives:
	
	1. Create a batch file with the following four lines:
	
	  setlocal
	  set comspec=c:\dos\command.com
	  c:\dos\command.com /c convert.bat
	  endlocal
	
	  If your COMMAND.COM file is contained in a directory other than DOS,
	  substitute the correct path in lines 2 and 3 above.
	
	2. Save the file and name it as CONV.BAT.
	
	3. Copy the CONV.BAT file to your Stacker conversion disk.
	
	4. To start the conversion program, change to your floppy drive by typing A: or
	  B: at the command prompt. Then type CONV at the command prompt.
	
	10. DoubleSpace cannot convert a Stacker 3.1 volume
	---------------------------------------------------
	
	If you receive the message "DoubleSpace cannot convert this Stacker 3.1 volume"
	when trying to convert a Stacker 3.1 floppy disk to DoubleSpace format, then the
	floppy disk is in a format that DoubleSpace cannot read.
	
	There are two ways to retrieve the files from such a floppy disk:
	
	- If a computer running Stacker 3.1 is available, take the floppy disk to the
	  other computer, and then run Stacker's SDEFRAG utility on the floppy disk.
	  When SDEFRAG asks if you want to restack the floppy disk, answer Yes. After
	  the floppy disk has been restacked, DoubleSpace can convert it to DoubleSpace
	  format.
	
	- If you don't have access to a computer that's running Stacker 3.1, you can
	  gain access to the files on the Stacker 3.1 floppy disk by carrying out the
	  following procedure.
	
	1. Remove any floppy disks from your drives, and then restart your computer by
	  pressing CTRL+ALT+DEL.
	
	2. When you see the message "Starting MS-DOS...", press CTRL+F5. Your computer
	  will start without DoubleSpace loaded; any DoubleSpace drives will be
	  temporarily unavailable.
	
	3. Insert the Stacker 3.1 floppy disk in drive A or drive B, and then type
	
	  " A:STACKER A:
	  " (without the quotation marks) or "B:STACKER B:" (without the quotation
	  marks)
	
	  The files on that floppy disk will now be available.
	
	4. Use the COPY command to copy the files on the Stacker 3.1 floppy disk to a
	  floppy disk in a different drive, or to a hard disk drive.
	
	5. Remove any floppy disks from your drives, and then restart your computer by
	  pressing CTRL+ALT+DEL.
	
	NOTE: If you copied the files to a hard disk drive that is normally a DoubleSpace
	drive, then after you restart your computer, the files will be located on that
	drive's host drive. For example, if you copied the files on the floppy disk to
	drive C, and drive C is normally compressed, then the files will be located on
	the host drive for drive C (probably drive H). To find out which is drive C's
	host drive, type DBLSPACE C: at the command prompt.
	
	
	Additional query words: 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS620
	Version           : :6.2
	
	=============================================================================
	

{% endraw %}
