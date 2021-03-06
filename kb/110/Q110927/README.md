---
layout: page
title: "Q110927: WFW RAS to Windows NT: &quot;Access Denied&quot; After Password Change"
permalink: /kb/110/Q110927/
---

## Q110927: WFW RAS to Windows NT: &quot;Access Denied&quot; After Password Change

{% raw %}

	Article: Q110927
	Product(s): Microsoft Programming Utilities
	Version(s): 1.0,1.1,1.1a,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Remote Access Service, versions 1.0, 1.1, 1.1a, used with:
	   - Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you dial in from your Windows for Workgroups client using Remote Access
	Service (RAS) to connect to a Windows NT or Windows NT Advanced Server version
	3.1 RAS server and your password is expired, the server will prompt you for a
	new password during the authentication process. After you give a new password
	you will be authenticated, but when your RAS client tries to automatically
	reconnect to a shared directory or when you use File Manager to browse the
	available shares on a server the following error message appears:
	
	  Access denied
	
	If you specify the full share point name:
	
	  \\<servername>\<sharename>
	
	you are prompted for the new password, and then successfully connected to the
	share.
	
	CAUSE
	=====
	
	This problem occurs because when you change your password over the RAS
	connection, the RAS client's local password file is not updated. Conversely,
	when you change your password over a direct network connection, your local
	password file is updated, so you are logged on with the new password and you are
	not denied access to new or persistent connections.
	
	
	WORKAROUND
	==========
	
	After giving a new password during authentication, choose Control Panel. In the
	Control Panel window choose the Network icon. Choose the Password button to
	change your password (again). Then log off and log on again from within the
	Network dialog box. These steps can be done during the same RAS connection.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Remote Access client
	for Windows for Workgroups 3.11. We are researching this problem and will post
	new information here in the Microsoft Knowledge Base as it becomes available.
	
	Additional query words: wfw wfwg 3.10 logon logoff
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbRASSearch
	Version           : :1.0,1.1,1.1a,3.11
	
	=============================================================================
	

{% endraw %}
