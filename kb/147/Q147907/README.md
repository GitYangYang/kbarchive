---
layout: page
title: "Q147907: Error Starting IIS Services Without TCP/IP Installed"
permalink: /kb/147/Q147907/
---

## Q147907: Error Starting IIS Services Without TCP/IP Installed

{% raw %}

	Article: Q147907
	Product(s): Internet Information Server
	Version(s): 1.0 3.51
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.51 
	- Microsoft Internet Information Server 1.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you attempt to start the Component Services of the Internet Information
	Server (IIS) 1.0 in Windows NT 3.51 without the TCP/IP protocol installed first,
	the following error message appears:
	
	  Could not start the World Wide Web Publishing Service service
	  on <computername>.
	
	  Error 10022:
	
	In addition, the following system events appear in Event Viewer:
	
	  Event ID: 4
	  Source: W3SVC
	  Description: HTTP Server was unable to initialize due to a shortage
	  of available memory. The data is the error: 26 27 00 00
	
	  Event ID: 7023
	  Source: Service Control Manager
	  Description: The World Wide Web Publishing Service service terminated
	  with the following error:
	
	  Event ID: 7023
	  Source: Service Control Manager
	  Description: The Gopher Publishing Service service terminated
	  with the following error:
	
	  Event ID: 7023
	  Source: Service Control Manager
	  Description: The FTP Publishing Service service terminated
	  with the following error:
	
	When you install the TCP/IP protocol after you install IIS, the following system
	events appear in Event Viewer:
	
	  Event ID: 3
	  Source: W3SVC
	  Description: HTTP Server could not initialize the socket
	  library. The data is the error: 7A 00 00
	
	  Event ID: 7023
	  Source: Service Control Manager
	  Description: The Gopher Publishing Service service terminated
	  with the following error: The data area passed to a system
	  call is too small.
	
	  Event ID: 7023
	  Source: Service Control Manager
	  Description: The FTP Publishing Service service terminated
	  with the following error: The data area passed to a system
	  call is too small.
	
	CAUSE
	=====
	
	The TCP/IP protocol must be installed before you install the Internet
	Information Server.
	
	RESOLUTION
	==========
	
	To correct this problem:
	
	1. Start Internet Information Server Setup.
	
	2. Click Remove All. This removes all previously installed components.
	
	3. Shut down and restart Windows NT.
	
	4. Reinstall the latest Windows NT Service Pack (currently SP4).
	
	5. Install the TCP/IP protocol in Control Panel Network.
	
	6. Shut down and restart Windows NT.
	
	7. Install Internet Information Server.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Internet Information Server
	version 1.0. We are researching this problem and will post new information here
	in the Microsoft Knowledge Base as it becomes available.
	
	Additional query words: prodiis winnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNTSsearch kbWinNTS351 kbWinNTS351search kbiisSearch kbiis100
	Version           : 1.0 3.51
	
	=============================================================================
	

{% endraw %}
