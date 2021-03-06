---
layout: page
title: "Q177277: How to Share a Network Printer to Novell and Microsoft Clients"
permalink: /kb/177/Q177277/
---

## Q177277: How to Share a Network Printer to Novell and Microsoft Clients

{% raw %}

	Article: Q177277
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbprint
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft BackOffice Small Business Server version 4.0 
	- Microsoft File and Print Services for NetWare versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to create and share a printer on a computer running
	both Windows NT Server and File and Print Services for NetWare (FPNW) for use by
	both Microsoft and NetWare network clients.
	
	To share a printer with File and Print Services for NetWare, you must first share
	the printer for Microsoft network clients. No other steps are required to share
	the printer with File and Print Services for NetWare.
	
	FPNW builds its list of shared network printers for NetWare clients by
	enumerating the list of printers shared for Microsoft network clients. FPNW
	advertises the printer name, rather than the share name, as the NetWare print
	queue name.
	
	MORE INFORMATION
	================
	
	To set up an FPNW printer to share to Novell NetWare clients, use the following
	steps:
	
	1. Create the printer using any method to establish connection with the printer
	  (that is, LPT1:, DLC, LPR, HP JetDirect Port, and so on).
	
	2. Name the printer. The Printer name is the name that NetWare network clients
	  will see when connecting to the print server.
	
	3. Share the printer. The Share name is the name Microsoft network clients will
	  see when browsing resources on the print server.
	
	NOTE: The FPNW Print Servers menu option available in Server Manager should not
	be used to create FPNW printer shares. This option is only used to configure
	FPNW to print to NetWare printers running Pserver.
	
	For information on printing to Pserver printers, query on the following words in
	the Microsoft Knowledge Base:
	
	  Pserver FPNW
	
	For information specifically on how to configure FPNW to service Pserver
	printers, please see the following articles in the Microsoft Knowledge Base:
	
	ARTICLE-ID: Q173531
	TITLE : How To Configure Printers on FPNW to Service Pserver.nlm
	
	ARTICLE-ID: Q140467
	TITLE : How to Set Up Printers on FPNW to Service PSERVER.EXE
	======================================================================
	Keywords          : kbnetwork kbprint 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbAudDeveloper kbSBServSearch kbSBServ400 kbServicesNetwareSearch kbFPNW351 kbFPNW400
	Version           : WinNT:3.5,3.51,4.0
	Hardware          : ALPHA PPC x86
	Issue type        : kbhowto kbinfo
	
	=============================================================================
	

{% endraw %}
