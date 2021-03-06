---
layout: page
title: "Q264630: SMS 2.0 SP1 and SP2 Interoperability Issues Without Updates"
permalink: /kb/264/Q264630/
---

## Q264630: SMS 2.0 SP1 and SP2 Interoperability Issues Without Updates

{% raw %}

	Article: Q264630
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200preSP2
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you apply Service Pack 2 (SP2) for Systems Management Server (SMS) 2.0, you
	may experience the following issues:
	
	Issue 1
	-------
	
	When multiple sites control a domain and SMS sites are not upgraded
	simultaneously, the Smslogon\Config\Copylog.tcf file is modified by the Service
	Pack 1 (SP1) site as well as the SP2 site. If the SP1 site modifies the
	Copylog.tcf file last (by using Microsoft Windows NT Logon Server Manager), it
	updates and changes most of the entries in the Copylog.tcf file.
	
	The Copylog.tcf file is used to indicate which site supplied the logon point's
	client boundaries (specially Clicore.exe). An SP1 site without the update can
	change the Copylog.tcf file to indicate that it supplied the logon point's
	Clicore file, even though it did not copy the file. The incorrect SP1
	Clicore.exe entry in the Copylog.tcf file causes problems for new installations
	as well as existing SP1 clients when they are using the logon point. This
	situation prevents new clients from being installed and causes SP1 clients to
	copy the SP2 Clicore.exe file, which results in a mixed installation state. Some
	common conditions seen on the client and in the client logs when in a mixed
	installation state include:
	
	- Components are in a "Repair Pending" state.
	
	- The Software Advertisement Program Wizard and Manager are unable to run.
	
	- A Required .dll file, Clilog.dll, is not found.
	
	Wn_logon and Wnmanual.log:
	
	No COMPVER.INI found for site SEC - defaulting logon point version to 2.00.0000.0000
	Could not register CCIM (could be initial install); AppRegister return code =5
	ERROR: Unable to open the service control manager to install the SMS Client Service and CCIM. Win32 Error: 5  
	Warning:  Could not launch/register CCIM - 5  
	
	SMSCLI.LOG
	ERROR: Failed to start C:\WINDOWS\MS\SMS\CLICOMP\SWDist32\bin\smswiz32.exe
	ERROR: Failed to start C:\WINDOWS\MS\SMS\CLICOMP\SWDist32\bin\smsmon32.exe
	
	Clisvc.log:
	
	ERROR: The Client Service is not authorized to run this application! (5)~
	*** Client Configuration Installation Manager - Error launching (#0x5)  C:\WINNT\MS\SMS\CORE\BIN\CLISVCL.EXE>
	WARNING: Problem starting App (5). Doing App Verify.  C:\WINNT\MS\SMS\CORE\BIN\CLISVCL.EXE>
	System Offer Data Provider - Not launching until CCIM indicates that it's safe to do so~
	
	CLICORE.LOG 
	Base client files are version 2.0.1493.2005
	Current clibase version is 2.0.1380.1101
	
	Launch32.log:
	
	WNet User Groups Offer Data Provider - Not launching until CCIM indicates that it's safe to do so~
	Program Execution Agent - Not Launching application~
	Lic Client - Not launching until CCIM indicates that it's safe to do so~
	Advertised Programs Monitor (Event Driven) - Not launching until CCIM indicates that it's safe to do so~
	Advertised Programs Monitor - Not launching until CCIM indicates that it's safe to do so~
	
	Ccim32.log:
	
	Client core file version (from cliver.exe) is 2.00.1493.2005
	Warning: The CAP base release (from \\SMSPDC20\CAP_PET\clicomp.box\base) is 2.00.1380.1 (client release is 2.00.1493.2)
	Warning - could not find a site CAP with uplevel version of component Available Programs Manager Win32
	Warning - could not find a site CAP with uplevel version of component Hardware Inventory Agent
	Warning - could not find a site CAP with uplevel version of component Software Distribution
	Warning - could not find a site CAP with uplevel version of component Software Inventory Agent
	Warning - could not find a site CAP with uplevel version of component Remote Control
	Warning - could not find a site CAP with uplevel version of component LICENSE METERING
	
	Trying to open IPC connection with APM...  CCIM32
	ERROR: Unable to establish a connection with APM - The filename, directory name, or volume label syntax is incorrect.~~  CCIM32
	Component "Hardware Inventory Agent" moved from index 4 to 6  CCIM32
	Trying to open IPC connection with APM...  CCIM32
	ERROR: Unable to establish a connection with APM - The filename, directory name, or volume label syntax is incorrect.~~  CCIM32
	Component "Software Distribution" moved from index 2 to 6  CCIM32
	Trying to open IPC connection with APM...  CCIM32
	ERROR: Unable to establish a connection with APM - The filename, directory name, or volume label syntax is incorrect.~~  CCIM32
	Component "Software Inventory Agent" moved from index 1 to 6  CCIM32
	Trying to open IPC connection with APM...  CCIM32
	ERROR: Unable to establish a connection with APM - The filename, directory name, or volume label syntax is incorrect.~~  CCIM32
	Component "Remote Control" moved from index 0 to 6  CCIM32
	Warning - CClientOfferArray::ResolvePendingOperations returned 123  CCIM32
	-- Checking if new component operations are necessary --       CCIM32
	-  SMS Client Base Components:           CCIM32
	Checking if component "SMS Client Base Components" needs to be installed, upgraded or verified (offer index [2])  CCIM32
	
	Issue 2
	-------
	
	When two sites share site boundaries and both sites use Remote Installation, SP1
	sites are unable to install SP1 components onto SP2 clients.
	
	The updates listed in articles Q252718 and Q252717 in the Microsoft Knowledge
	Base add functionality to the Client Configuration Manager (CCM) and
	Ccmbtldr.exe components that verify that the client does not have files from a
	later release. The SP1 update prevents SP1 from attempting to remotely install
	on SP2 clients. This functionality is included with SP2 and this will not be an
	issue for future service pack releases.
	
	Applying the update after this problem is already occurring stops it from
	retrying to install onto the client, but existing Client Configuration Requests
	(CCR) that have already started processing attempt every hour for a total of 7
	days before they time out. Not applying the update does not cause clients to get
	into a mixed installation state. Only the issues described in articles Q251070
	and Q249077 in the Microsoft Knowledge Base (the Copylog.tcf issue) causes
	clients to get into a mixed installation state. Common issues observed on
	clients include:
	
	- Software advertisements do not reach the clients.
	
	- Orphaned clients that do not recover from mixed installation.
	
	
	CAUSE
	=====
	
	These issues can occur if both of the following conditions are true:
	
	- Required SMS updates to SMS sites that exist in the same domain were not
	  installed before you upgraded to SP2 for SMS:
	
	   - Issue 1: These issues can occur if you did not install the updates listed
	     in the following Microsoft Knowledge Base articles:
	
	SMS 2.0 (No Service Pack) Sites:
	
	  Q251070 SMS: Copylog.tcf Does Not Show Site that Updated Logon Point
	
	SP1 Sites:
	
	  Q249077 SMS: SP1:Copylog.tcf Does Not Show Site that Updated Logon Point
	
	   - Issue 2: These issues can occur if you did not install the updates listed
	     in the following Microsoft Knowledge Base articles:
	
	SMS 2.0 (No Service Pack) Sites:
	
	  Q252718 SMS: CCM Avoids Installation Attempts on SP2 Clients
	
	SP1 Sites:
	
	  Q252717 SMS: SP1: CCM Avoids Installation Attempts on SP2 Clients
	
	- All SMS sites in a domain are not or were not upgraded beginning with the
	  central parent site within several hours of each other.
	
	WORKAROUND
	==========
	
	To resolve these issues, use the appropriate method.
	
	Issue 1
	-------
	
	- Applying the update after a client is in the mixed state does not repair the
	  clients that are in a mixed state. Also, applying the updates before
	  upgrading to SP2 prevents new installations to clients that are assigned to a
	  SP1 site until the client's assigned site is upgraded to SP2. If the client
	  has two sites and one is at SP1 and the other is at SP2, the client upgrades
	  successfully to SP2.
	
	- If for some reason the updates cannot be applied to remote systems for some
	  period of time due to distance, or unavailability of technical support
	  personnel at the remote location, you can remotely edit the Copylog.tcf file:
	
	  1. Edit the Copylog.tcf file on the primary domain controller (PDC) in the
	     \\PDC\SMSLOGON\Config folder by using a text editor such as Notepad.exe,
	     and modify the following line
	
	  X86.BIN\CLICORE.EXE=<XXX>
	
	     where <XXX> is the site code for the SP2 site.
	
	  2. Change the permissions on the Copylog.tcf file to Read Only and assign
	     Full Control permission only to a domain user account that has Domain
	     Admin privileges, however, do not use the Administrator or the SMS service
	     account. Also, assign Read privileges to the Everyone group. Note that new
	     installations to clients which fall into the subnet boundary for an SP1
	     site do not occur until the SP1 site assigned is upgraded to SP2.
	
	     NOTE: After you upgrade the site to SP2, change the file permissions back
	     to their original permissions.
	
	  3. Upgrade all sites to SP2, which repairs and upgrades the clients when they
	     are in the mixed mode, except in some cases where the user who is logged
	     on is not a local Administrator on the computer.
	
	Issue 2
	-------
	
	- Applying the update after CCM attempts to install onto the SP2 client
	  resolves the problem and prevents further occurrences, however all of the
	  files in the Ccrretry.box file need to be deleted as well or the installation
	  attempts are retried every hour for 7 days.
	
	- Upgrade all sites to SP2 which permits remote installations to succeed on
	  clients with SP2 files.
	
	- Rename the Ccm.dll file to Ccm.old on the SMS SP1 servers, which prevents it
	  from downloading the new Clicore.exe file. However, remote installation for
	  all clients stops.
	
	MORE INFORMATION
	================
	
	Planning for the Upgrade to Service Pack 2
	------------------------------------------
	
	If the SMS 2.0 sites are all going to be upgraded within a 2-hour to 3-hour
	period, it is unlikely for mixed installations to occur on clients. A weekend
	upgrade may be a good idea if the updates cannot be applied to all sites
	quickly.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200preSP2 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
