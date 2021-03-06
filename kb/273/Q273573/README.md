---
layout: page
title: "Q273573: IISADMPWD Password Change Pages Fail to Change Passwords"
permalink: /kb/273/Q273573/
---

## Q273573: IISADMPWD Password Change Pages Fail to Change Passwords

{% raw %}

	Article: Q273573
	Product(s): Internet Information Server
	Version(s): 4.0,5,5.01,5.5
	Operating System(s): 
	Keyword(s): kbie500 kbiis400 kbie501 kbie550kbfaq
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 4.0 
	- Microsoft Internet Explorer versions 5, 5.01 for Windows 95 
	- Microsoft Internet Explorer versions 5, 5.01, 5.5 for Windows NT 4.0 
	- Microsoft Internet Explorer versions 5, 5.01 for Windows 98 
	- Microsoft Internet Explorer versions 5, 5.01 for Windows 2000 
	- Microsoft Internet Explorer version 5 for Windows 98 Second Edition 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	User password changes fail are not accepted when using the password change pages
	provided under the IISADMPWD subweb in the default Web site.
	
	CAUSE
	=====
	
	This problem only occurs if the IISADMPWD subweb is set to use NTLM
	authentication, and the client is using Internet Explorer 5.0, 5.01, 5.01 SP1 or
	5.5.
	
	Internet Explorer 5.0 has a new feature named NTLM pre-authorization, which
	requires NTLM authentication for all visits after you visit one NTLM
	authenticated folder.
	
	RESOLUTION
	==========
	
	Make the following registry changes on the client workstation that is using
	Internet Explorer.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. Run the Registry Editor (Regedit.exe or Regedt32.exe)
	
	2. Locate the following key in the registry:
	
	  HKEY_CURRENT_USER/Software/Microsoft/Windows/CurrentVersion/Internet
	  Settings/
	
	3. Add the following registry value:
	
	  Value Name: DisableNTLMPreAuth
	  Data Type: REG_DWORD
	  Value: 1
	
	MORE INFORMATION
	================
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q251404 HTML File Cannot Post Data to a Non-NTLM Authenticated Folder for
	  further details.
	
	  Q184619 How to Change Windows NT Account Passwords Using IIS 4.0
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbie500 kbiis400 kbie501 kbie550 kbfaq
	Technology        : kbiisSearch kbIEsearch kbiis400 kbZNotKeyword2 kbIENT400Search kbIE95Search kbIE500Search kbZNotKeyword3 kbIE2000Search kbIE98Search kbIE500Win2000 kbIE501Win2000 kbIE500Win95 kbIE500Win98 kbIE501Win98 kbIE500Win98SE kbIE500WinNT400 kbIE501WinNT400 kbIE550WinNT400 kbIE98SESearch kbIE501Win95 kbZnotKeyword7 kbIE550Search
	Version           : :4.0,5,5.01,5.5
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
