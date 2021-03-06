---
layout: page
title: "Q194381: Err Msg: Unknown HTTP Server Type Msiis"
permalink: /kb/194/Q194381/
---

## Q194381: Err Msg: Unknown HTTP Server Type Msiis

{% raw %}

	Article: Q194381
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 98 version of this article, see Q194972.
	
	SYMPTOMS
	========
	
	When you try to install Microsoft FrontPage Server Extensions from the FrontPage
	Server Administrator or by running the Setup program from the FrontPage compact
	disc, the following error occurs:
	
	  Unknown HTTP server type msiis
	
	  -OR-
	
	  When you try to install Microsoft FrontPage Server Extensions from the
	  FrontPage Server Administrator and try to select a server, the only choice
	  available is the FrontPage Personal Web Server.
	
	CAUSE
	=====
	
	The problem is caused by one of the following:
	
	- A corrupted or empty Servers.cnf file in the C:\Program Files\Microsoft
	  FrontPage\Version3.0\Servsupp directory.
	
	- A corrupted download of the server extensions.
	
	- A corrupted [Ports] section in the C:\Winnt\Frontpg.ini directory.
	
	- Permissions on the C:\Program Files\Microsoft Frontpage\Version3.0\Servsupp
	  directory are incorrect.
	
	- You are not logged on as an administrator.
	
	RESOLUTION
	==========
	
	To resolve this problem, use any or all of the following methods:
	
	Method 1 (Corrupt or empty Servers.cnf file)
	--------------------------------------------
	
	In the %Program Files%\Microsoft FrontPage\Version3.0\Servsupp folder locate the
	file named Servers.cnf. If this file is empty, ensure that the administrator has
	Full Control set on the Servsupp directory and all the files in the directory.
	Run the FrontPage Server Administrator, and if the Servers.cnf file is still
	empty, remove and reinstall the FrontPage Server Extensions.
	
	Method 2 (Corrupted download of the FrontPage Server Extensions)
	----------------------------------------------------------------
	
	1. Run the FrontPage Server Administrator to remove the extensions.
	
	2. Click the Start button, choose Settings, and then select Control Panel.
	
	3. Double-click Add/Remove Programs and remove the extensions.
	
	4. Ensure that the %Program Files%\Microsoft FrontPage\Version3.0\Servsupp
	  directory has been removed by the Uninstall operation. If it has not, delete
	  that directory through the Windows file system. If access is denied when you
	  attempt to do this, stop the Web server running on the system and delete the
	  folder. Restart the Web server when you have successfully deleted the folder.
	
	5. Go to http://www.microsoft.com/frontpage/wpp/license.htm and download the new
	  FrontPage Server Extensions.
	
	6. Reinstall the new extensions per the Readme.txt file.
	
	Method 3
	--------
	
	1. Open your %Windows Dir%\Frontpg.ini file in Notepad. In that file, there is a
	  parameter block labeled [Ports]; this is the list of IP/port combinations
	  that you currently have extensions installed for. If you see your base IP, or
	  if you are not multihoming and you see Port80= and Port 443=, delete those
	  lines.
	
	2. Reinstall the new extensions per the Readme.txt file.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbFrontPageSearch kbFrontPage97 kbZNotKeyword2 kbFrontPage97Search
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
