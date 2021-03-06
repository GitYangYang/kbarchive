---
layout: page
title: "Q276502: FP: Server Error: Unable to Retrieve the List of Record Sources"
permalink: /kb/276/Q276502/
---

## Q276502: FP: Server Error: Unable to Retrieve the List of Record Sources

{% raw %}

	Article: Q276502
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 01-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 2002 
	- Microsoft FrontPage 2000 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	In Microsoft FrontPage, when you attempt to add a new or use an existing data
	connection that uses a System DSN (Data Source Name), you receive an error
	message similar to the following:
	
	  Server error: Unable to retrieve the list of record sources from a database
	  using the connection string:
	
	  DSN=NORTHWIND;DRIVER={Microsoft Access Driver (*.mdb)}.
	
	  The following error message comes from the database driver software; it may
	  appear in a different language depending on how the driver is configured.
	
	  Source: ADO
	  Number: -2146824584 (0x800a0e78)
	
	CAUSE
	=====
	
	This problem can occur if the following conditions are true:
	
	- You are using a System DSN (Data Source Name) to connect to a Microsoft
	  Access database.
	- The Microsoft Access database is located on a remote server.
	- You are connecting to the database from an Internet Information Services
	  (IIS) server on which the following authentication settings are configured:
	
	   - Anonymous Authentication is enabled.
	   - Basic Authentication is disabled.
	   - Integrated Windows Authentication (NTLM), or Digest Authentication is
	     enabled.
	
	IIS runs a system service. If anonymous access is enabled, it attempts to connect
	to the remote database using the local System account. Because that account does
	not have access to the remote server, the error message described in the
	"Symptoms" section earlier in this article appears. Also, this problem can occur
	if only Integrated Windows Authentication (NTLM) is enabled because IIS cannot
	delegate your credentials to a remote server.
	
	WORKAROUND
	==========
	
	To work around this problem, use either of the following methods.
	
	Method 1: Configure IIS for Basic Authentication Only
	-----------------------------------------------------
	
	When you use Basic/Clear Text Authentication, IIS can delegate your credentials
	to the remote server. For this to function correctly, configure the following
	security options in IIS:
	
	- Disable Anonymous access.
	
	- Enable Basic/Clear Text authentication.
	
	- Disable Digest authentication.
	
	- Disable NTLM or Windows Integrated authentication.
	
	To configure IIS for Basic/Clear Text Authentication, refer to the documentation
	for your version of IIS. For additional information about how to configure this
	on Windows 2000, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q262233 IIS: How to Configure Basic/Clear Text Authentication for IIS 5.0 in
	  Windows 2000
	
	Method 2: Configure a Null Session Share
	----------------------------------------
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	WARNING: The following procedure creates a file share that has no security
	settings and, therefore, allows anyone anonymous network access to your remote
	database. Microsoft does not recommend that you use this procedure if you have a
	production environment or an Internet-based Web server.
	
	A Null Session Share allows anyone to anonymously connect to a database.
	Therefore, you should store the database in a hidden share. To configure a Null
	Session Share to allow access to the database on the remote server, follow these
	steps:
	
	1. Create a hidden share to hide your database:
	
	  a. On the remote server, log on locally as an administrator.
	
	  b. Right-click the Start button and then click Explore. Create a folder to
	     host your database. For example, create a folder called
	
	  C:\InetPub\WebData$
	
	     NOTE: A dollar sign ("$") at the end of the file name will help create a
	     hidden share.
	
	     For increased security, use a unique name for the folder, such as
	     C:\InetPub\Cv5Mq0Qa$.
	
	
	  c. Copy your database to the new folder.
	
	  d. Right-click the new folder and click Sharing on the menu that appears.
	
	  e. Choose the option to share the folder.
	
	  f. Hide the share. To do this, give the share a name that ends with a dollar
	     sign ("$"). For example, name the share WebData$.
	
	     Or, for increased security, name the share using a random name, such as,
	     Cv5Mq0Qa$.
	
	  g. Click OK.
	
	  h. Quit Windows Explorer.
	
	2. Configure the hidden share as a Null Session Share:
	
	  a. Start Registry Editor (Regedt32.exe).
	
	  b. Select the following registry subkey:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\LanmanServer\Parameters
	
	  c. Select the NullSessionShares Name value and then click Multi-string on the
	     Edit menu.
	
	  d. Type the hidden share name. For example, type "WebData$" (without the
	     quotation marks).
	
	  e. Click OK.
	
	  f. Quit Registry Editor.
	
	3. Restart the server.
	
	When you create a system DSN from the IIS web server to the database on the
	remote server, use the path to the hidden share name. For example, use
	\\servername\WebData$.
	
	MORE INFORMATION
	================
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q207671 HOWTO: Accessing Network Files from IIS Applications
	
	  Q124184 Service Running as System Account Fails Accessing Network
	
	  Q132679 Local System Account and Null Sessions in Windows NT
	
	
	
	Additional query words: front page
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch kbFrontPage2002 kbFrontPage2000Search kbFrontPage2002Search kbZNotKeyword5
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
