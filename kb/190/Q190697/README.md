---
layout: page
title: "Q190697: XADM: Mt.exe Unable to Locate DLL on Startup"
permalink: /kb/190/Q190697/
---

## Q190697: XADM: Mt.exe Unable to Locate DLL on Startup

{% raw %}

	Article: Q190697
	Product(s): Microsoft Exchange
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft BackOffice Small Business Server versions 4.0, 4.0a 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you perform a complete custom installation of Exchange Server through the
	Exchange Server Setup, the following error message may appear:
	
	  Window title: MT.EXE unable to locate DLL
	  Description: The dynamic link library address.dll could not be found in
	  the specified path
	  c:\exchsrvr\connect\msmcon\bin;;c:\winnt.sbs\system32;c:\winnt.sbs\system;
	  c:\winnt.sbs;c:\winnt.sbs\system32;c:\winnt.sbs;c:\mssql\binn.
	
	After you click OK, the following error message from Service Control Manager
	appears:
	
	  At least one service or driver failed during system startup. Use event
	  viewer to examine the event log for details.
	
	The event viewer system log shows the following:
	
	  Event ID 7000
	  Source: Service control manager
	  Description:
	  The MS Mail connector Interchange service failed to start due to the
	  following error: The service did not respond to the start or control
	  request in a timely fashion.
	
	followed by:
	
	  Event ID 7009
	  Source: Service control manager
	  Description:
	  Timeout (120000 milliseconds) waiting for service to connect.
	
	CAUSE
	=====
	
	When you perform a complete custom installation through Exchange Setup, the
	Exchange Setup installs the Microsoft Exchange Connector for Lotus cc:Mail and
	the Microsoft Mail Connector by default and sets the Microsoft Mail Connector
	service (MS Mail Connector interchange) to automatic by default. Small Business
	Server does not allow these services to run; thus, the error messages appear.
	
	WORKAROUND
	==========
	
	There are four possible ways to work around this problem:
	
	- Set the MS Mail Connector interchange service to manual start. To do this, go
	  to Control Panel, click Services, and select MS Mail Connector Interchange
	  service. Click Startup with this service highlighted. Then set startup type
	  to manual. Click OK and restart.
	
	- Reinstall Exchange Server using a Complete Custom installation. Click the
	  Change Options button for the Exchange Server during Setup, clear (uncheck)
	  the check boxes for the connectors, and continue Setup.
	
	- Uninstall Exchange Server and reinstall as follows:
	
	  1. On Control Panel, select Add/Remove programs.
	
	  2. On the Install/Uninstall tab, select Microsoft Small Business Server
	     Setup.
	
	  3. On the Microsoft Small Business Server setup window, select Exchange
	     Server and click Next.
	
	  4. Enter the administrator password and click Next.
	
	- The Small Business version of Exchange Server can be upgraded to Full Package
	  Exchange Server. The full package product allows for Microsoft Mail
	  Connector, Microsoft Exchange Connector for Lotus cc:Mail, or other
	  connectors, depending on the version installed. Contact Microsoft Sales or
	  visit the following Web site for more upgrade information:
	
	  http://www.microsoft.com/smallbusinessserver
	
	
	Additional query words: sbs smallbiz xadm xfor
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSBServSearch kbSBServ400 kbSBServ400a
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
