---
layout: page
title: "Q164294: FP: How to Change ServerName for FrontPage Personal Web Server"
permalink: /kb/164/Q164294/
---

## Q164294: FP: How to Change ServerName for FrontPage Personal Web Server

{% raw %}

	Article: Q164294
	Product(s): Word Front Page
	Version(s): windows:1.0,1.0a,1.1,97
	Operating System(s): 
	Keyword(s): kbfile kbusage kbdta
	Last Modified: 04-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows with Bonus Pack 
	- Microsoft FrontPage for Windows 1.1 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 98 version of this article, see Q194542.
	
	SUMMARY
	=======
	
	This article describes how to change the ServerName of the FrontPage Personal
	Web Server.
	
	MORE INFORMATION
	================
	
	ServerName affects the name the server returns to a client. For example, if a
	Web browser requests http://www.microsoft.com/frontpage, the server redirects
	that to http://www.microsoft.com/frontpage/ (with a trailing slash) so that
	relative links are interpreted correctly. The server does not know the name that
	was sent in the original request (without the trailing slash), so it typically
	uses the host name as returned by the Transport Control Protocol (TCP).
	
	This can lead to problems in three cases:
	
	- Your machine is known by multiple names and you want to control which name is
	  returned (for example, mail.example.com and www.example.com).
	- Your TCP is configured incorrectly so the server cannot determine its server
	  name.
	- You are using the FrontPage 1.0 Personal Web Server (PWS), and your hostname
	  is not qualified (does not contain any dots). The original PWS would reject
	  nonqualified domain names because they would be misinterpreted if they were
	  sent outside the local domain.
	
	The recommended solution to case 2 above is to fix your TCP/IP configuration. As
	an interim workaround, you might change the ServerName, but this is not
	preferred and will lead to problems on a networked machine.
	
	Use the following steps to change the ServerName for the FrontPage Personal Web
	Server:
	
	1. Using a text editor, such as Notepad, open the Httpd.cnf file. This file is
	  located in the c:\FrontPage Webs\Server\conf subdirectory.
	
	  In FrontPage 1.0, this file is located in the C:\Vermeer\http\conf
	  subdirectory.
	
	2. Locate the section which describes the ServerName directive. It looks like
	  this:
	
	     # ServerName allows you to set a host name that is sent back to
	     # clients for your server. If it's different than the one the
	     # program would get (i.e. use "www" instead of the host's real
	     # name). Make sure your DNS is set up to alias the name to your
	     # system!
	     #
	     # Format: ServerName <domain_name>
	     #
	     # no default
	
	3. Add the following line:
	
	  ServerName <domain_name>
	
	  where <domain_name> is the name of your domain.
	
	  NOTE: The server name cannot contain spaces.
	
	  If you are naming your server "localhost" (without the quotation marks), type
	  this line so that it looks like this:
	
	  ServerName localhost
	
	4. Save and close the file.
	
	Restart the FrontPage Personal Web Server. It will respond to the name you typed
	in step 3.
	
	NOTE: If your computer does not have DNS enabled and your TCP/IP stack supports
	it, you can use "localhost" (without the quotation marks) as your computer name
	without having to make the changes described in this article. You will also be
	able to specify "localhost" if your computer has a host name that is not fully
	qualified. To determine if your TCP/IP stack supports this configuration, run
	the FrontPage 1.1 TCP/IP test. In FrontPage 97, start the FrontPage Explorer,
	click About Microsoft FrontPage Explorer on the Help menu, and then click
	Network Test.
	
	Additional query words: 1.00 1.00a 97
	
	======================================================================
	Keywords          : kbfile kbusage kbdta 
	Technology        : kbFrontPageSearch kbFrontPage1xSearch kbFrontPage97Search kbZNotKeyword3 kbFrontPage110
	Version           : windows:1.0,1.0a,1.1,97
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
