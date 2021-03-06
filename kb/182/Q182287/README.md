---
layout: page
title: "Q182287: Setting up a Canon LBP360PS Printer for LPR Printing"
permalink: /kb/182/Q182287/
---

## Q182287: Setting up a Canon LBP360PS Printer for LPR Printing

{% raw %}

	Article: Q182287
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbprint
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you print to a Canon Laser Beam LBP 360 PS printer on a line printer remote
	(LPR) printer port, the following error message may occur in the print queue:
	
	  Printer Error
	
	You may also receive the following event in the Application event log on the
	server:
	
	  Event ID: 2004
	  Description: Printer on <printer name> is rejecting your request.
	               Will retry until it accepts the request or the job
	               is canceled by the user.
	
	RESOLUTION
	==========
	
	The Canon Laserbeam LBP 360 PS printer has a predefined IP address, subnet mask,
	and default gateway. When you set up this printer as a TCP/IP printer, the LPR
	port server name must be specifically named. Follow the steps below to create
	the LPR Port:
	
	1. Click Start, point to Setting, and then click Printers for Windows NT 4.0.
	
	  -or-
	
	  Double-click Control Panel in the Main group, and then double-click Print
	  Manager for Windows NT 3.51.
	
	2. Double-click Add Printer and select My Computer, click Next, and then click
	  Add Port.
	
	  -or-
	
	  On the Printer menu, click Create Printer, and then click Other in the Print
	  To list.
	
	3. Click LPR Port, and then click New Port.
	
	4. Type the following information:
	
	   - Name or address of server providing LPD: <IP address>
	
	   - Name of printer or print queue on that server: xjprint
	
	     NOTE: The printer name, xjprint, must be typed in lowercase.
	
	For more information about configuring up a Canon Laser Beam printer as an LPD
	device, please consult the Canon Laser Beam manual provided with the printer or
	contact Canon for assistance.
	
	Canon Laser Beam is manufactured by Canon, Inc. a vendor independent of
	Microsoft; we make no warranty, implied or otherwise, regarding this product's
	performance or reliability.
	
	Additional query words: 360ps LBP360
	======================================================================
	Keywords          : kb3rdparty kbprint 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : WinNT:3.5,3.51,4.0
	Hardware          : ALPHA x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
