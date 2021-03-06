---
layout: page
title: "Q184205: XADM: Information Store Fails to Start with Error 2186"
permalink: /kb/184/Q184205/
---

## Q184205: XADM: Information Store Fails to Start with Error 2186

{% raw %}

	Article: Q184205
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 09-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Exchange System Attendant service in Control Panel starts, but it
	logs the following error message in the application event log:
	
	  Event ID: 1000
	  Source: Userenv
	  Category: None
	  Description:
	  Your profile was not successfully loaded, but you have been logged on
	  with the default system profile. Please correct the problem and log off.
	  (5)
	
	Starting the Microsoft Exchange directory service in Control Panel gives no
	errors and logs no events.
	
	When you try to start the Microsoft Exchange information store service in Control
	Panel, the following error messages appear:
	
	  An application error has occurred and an application error log is being
	  generated.
	  Store.exe
	  Exception: access violation (0xc0000005), Address: 0x77f6cbfe
	
	  Cannot start the Microsoft Exchange Information Store service on
	  \\<computername>.
	  Error 2186: The service is not responding to the control function.
	
	The following messages are logged in the application event log:
	
	  Event ID: 1133
	  Source: MSExchangeIS
	  Category: General
	  Description:
	  Error 4021 connecting to the Microsoft Exchange Server Directory
	  Service.
	
	  Event ID: 5000
	  Source: MSExchangeIS
	  Category: None
	  Description:
	  Unable to initialize the Microsoft Exchange Information Store service.
	  Error 4021.
	
	  Event ID: 1005
	  Source: MSExchangeSA
	  Category: Monitoring
	  Description:
	  Unexpected error <<0xc0040000 - The Microsoft Exchange Server computer
	  is not available. Either there are network problems or the Microsoft
	  Exchange Server computer is down for maintenance. Microsoft Exchange
	  Server Information Store ID no: 8004011d-0524-00000000>> occurred.
	
	The following messages are logged in the system event log:
	
	  Event ID: 7009
	  Source: Service Control Manager
	  Category: None
	  Description:
	  Timeout (120000 milliseconds) waiting for service to connect.
	
	  Event ID: 7000
	  Source: Service Control Manager
	  Category: None
	  Description:
	  The Microsoft Exchange Information Store service failed to start due to
	  the following error:
	  The service did not respond to the start or control request in a timely
	  fashion.
	
	CAUSE
	=====
	
	The System Account or LocalSystem Account is specified as the service account in
	Control Panel Startup for each of these services.
	
	WORKAROUND
	==========
	
	To resolve this problem, perform the following procedure for each of these
	services:
	
	1. Select the service in Control Panel and click Startup.
	
	2. Verify that the service account is correct.
	
	3. Retype the password and password confirmation.
	
	4. Go to User Manager for Domains.
	
	5. Click on Policies from the title bar menu, and select User Rights.
	
	6. Select the option for Advanced User Rights.
	
	7. In the drop-down list, verify that the following rights have been granted to
	  the service account:
	
	  Act as part of the operating system
	  Back up files and directories
	  Log on as a service
	  Restore files and directories
	
	The services should now start without error.
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : WINDOWS:4.0,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
