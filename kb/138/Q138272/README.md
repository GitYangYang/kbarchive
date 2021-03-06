---
layout: page
title: "Q138272: Browse List Contains Obsolete Domain Names"
permalink: /kb/138/Q138272/
---

## Q138272: Browse List Contains Obsolete Domain Names

{% raw %}

	Article: Q138272
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.51
	Operating System(s): 
	Keyword(s): kbother
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.51 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you browse the network, only incomplete browse lists appear or the browse
	list contains domains that are no longer valid.
	
	Incomplete browse list example:
	
	  On a network with 2000 domains (2000 is the maximum number of domains that
	  Browser can accommodate) less than 2000 domains appear on the browse list.
	
	CAUSE
	=====
	
	You are stopping the WINS service daily to do off-line compaction (Jetpack).
	
	The WINS service triggers a scavenge of obsolete records if the time that elapsed
	from the WINS service startup has reached half of the renewal interval. The
	renewal interval is set to 96 hours by default, therefore the scavenge is
	performed after the WINS service runs continuously for 48 hours. If you stop the
	WINS service daily, that is every 24 hours, the scavenger never gets a chance to
	run and the domain records are never scavenged. Therefore, obsolete domains
	appear in the browser list and in the WINS Admin tool with old expiration dates,
	but still marked ACTIVE.
	
	
	WORKAROUND
	==========
	
	To work around this problem, enterprise Administrators have the option to do one
	or more of the following:
	
	- Decrease the Renewal and Extinction intervals.
	
	- Leave the WINS server up longer than the half the renewal interval.
	
	- Manually initiate scavenging through the WINS Admin tool.
	
	- Use an AT scheduler script to trigger the scavenge with WINSCL.EXE. For
	  additional information on WINSCL.EXE read the section titled The WINSCL.EXE
	  Command Line Utility below.
	
	- In large enterprises, daily jetpacking of the WINS database may be necessary
	  to keep the size of the WINS.MDB from becoming excessively large; this also
	  helps maintain query performance and database integrity. Currently, the Jet
	  database engine under WINS only supports off-line compaction.
	
	
	The WINSCL.EXE Command Line Utility
	-----------------------------------
	
	WINSCL.EXE is a command line utility for WINS database management. It is included
	in the Windows NT 3.51 Resource Kit. A sample script, SCAVWINS.CMD, is given
	below. You should replace the xxx.xxx.xxx.xxx in the fifth line of the following
	script with the appropriate IP address for your server:
	
	  @echo off
	  REM Script for Initiating Scanvenging on WINS
	  REM
	
	  REM Local WINS IP address
	  set winsip=xxx.xxx.xxx.xxx
	
	  REM directory where winscl.exe is located
	  set homedir=%systemroot%\system32\wins
	
	  REM Create init file
	  echo 1 >%homedir%\scav.in
	  echo %winsip% >>%homedir%\scav.in
	  echo SC >>%homedir%\scav.in
	  echo EX >>%homedir%\scav.in
	
	  REM execute winscl
	  %homedir%\winscl <%homedir%\scav.in >%homedir%\scavwins.log
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. A fix
	to this problem is in development, but has not been regression-tested and may be
	destabilizing in production environments. Microsoft does not recommend
	implementing this fix at this time. Contact Microsoft Product Support Services
	for more information on the availability of this fix.
	
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbother 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNTSsearch kbWinNTS351 kbWinNTS351search
	Version           : winnt:3.51
	
	=============================================================================
	

{% endraw %}
