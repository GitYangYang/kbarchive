---
layout: page
title: "Q184321: Can't Connect to SSL-Enabled Site and/or Server Stops Responding"
permalink: /kb/184/Q184321/
---

## Q184321: Can't Connect to SSL-Enabled Site and/or Server Stops Responding

{% raw %}

	Article: Q184321
	Product(s): Internet Information Server
	Version(s): 3.0,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 3.0, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On a Web site that has Secure Sockets Layer (SSL) enabled, either of the
	following problems may occur:
	
	- The server stops responding intermittently, and attempting to browse the site
	  causes the following message:
	
	     Web Site found....waiting for reply.
	
	  This message is followed by:
	
	     Unable to connect to server.
	
	  However, the World Wide Web Publishing Service appears to be running
	  correctly; it can be stopped and started, and there are no related errors in
	  the Event Log.
	
	  -or-
	
	- Attempting to browse the site causes:
	
	   - A message stating that a connection with the server could not be
	     established.
	
	     -or-
	
	   - The browser stops responding when you attempt to connect to the site.
	
	WORKAROUND
	==========
	
	To work around this problem, try the following (each option is described in more
	detail below):
	
	- Verify that the Schannel.dll file is current.
	
	- Verify that the ISAPI filter Sspifilt.dll is installed.
	
	- Remove and reinstall the certificate key.
	
	Verify That Schannel.dll Is Current
	-----------------------------------
	
	Verify that you are you have the latest version of Schannel.dll, the PCT/SSL
	Security Provider, for your version of Internet Information Server (IIS).
	
	For IIS 3.0, Schannel.dll has the following file properties:
	
	- Date: 4/30/97 or 5/1/97
	
	- Size: 128,272 bytes
	
	For IIS 4.0, Schannel.dll has the following file properties:
	
	- Date: 11/18/97
	
	- Size: 160,840 bytes
	
	Verify that the ISAPI Filter Sspifilt.dll Is Installed
	------------------------------------------------------
	
	The active copy of Sspifilt.dll should be located in the \Winnt\System32\Inetsrv
	directory.
	
	For IIS 3.0:
	
	The following registry entry should be present and include the path to the active
	Sspifilt.dll file:
	
	  HKEY_Local_Machine\System\CurrentControlSet\Services\W3SVC\Parameters\Filter
	  Dlls
	
	For IIS 4.0:
	
	From the Master Properties of the WWW service, on the ISAPI Filters tab, verify
	that there is an entry pointing to the active copy of the Sspifilt.dll file.
	This entry should be loaded and running (as indicated by a green up-arrow).
	
	Remove and Reinstall Certificate Key
	------------------------------------
	
	1. For Internet Information Server version 3.0 (IIS), you may want to reinstall
	  Service Pack 3 to ensure that all files are current.
	
	2. Using Key Manager, export the Certification Authority (CA) key (also known as
	  a certificate) to a backup file.
	
	3. Delete the key, then close Key Manager. When prompted to "Commit all changes
	  now?", click Yes.
	
	4. Stop and start the World Wide Web Publishing Service.
	
	5. In Key Manager, import the key you backed up in Step 2 of this procedure.
	
	6. Close Key Manager, being sure to again click Yes when you are prompted to
	  "Commit all changes now?"
	
	7. Stop and start the World Wide Web Publishing Service.
	
	Additional query words: https hang hangs hung fails akz
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis400 kbiis300
	Version           : :3.0,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
