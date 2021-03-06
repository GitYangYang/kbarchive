---
layout: page
title: "Q148420: XCLN: Can't Change Password on Novell Client"
permalink: /kb/148/Q148420/
---

## Q148420: XCLN: Can't Change Password on Novell Client

{% raw %}

	Article: Q148420
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0,8.0; :
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 09-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 3.x client, versions 4.0, 5.0 
	- Microsoft Exchange Windows 95/98 client, versions 4.0, 5.0 
	- Microsoft Exchange Windows NT client, versions 4.0, 5.0 
	- Microsoft Outlook, Exchange Server Edition, version 8.0, used with:
	   - the operating system: Microsoft Windows versions 3.1, 3.11 
	- Microsoft Outlook 97 
	- Microsoft Outlook 98 
	- Microsoft Outlook 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to change the password on a Microsoft Exchange or Outlook client
	that is logging on to a Novell server and not being authenticated by a Windows
	NT server at bootup, the following error message may occur:
	
	  The NT Domain password could not be changed. A required action was not
	  successful due to an unspecified error.
	
	This may also occur with other clients running on other operation systems and
	networking software using TCP/IP or IPX as their protocol.
	
	RESOLUTION
	==========
	
	To resolve this problem, do the following:
	
	1. For NetWare clients, install the Gateway Services for NetWare on the primary
	  domain controller (PDC), which has the Microsoft Exchange user accounts.
	
	2. Ensure that the client is running the latest version of the networking files
	  from the software provider.
	
	3. Ensure that the Remote Procedure Call (RPC) service is configured to start
	  automatically. This can be changed in Control Panel Services.
	
	  WARNING: Using Registry Editor incorrectly can cause serious problems that may
	  require you to reinstall Windows NT. Microsoft cannot guarantee that problems
	  resulting from the incorrect use of Registry Editor can be solved. Use
	  Registry Editor at your own risk.
	
	  NOTE: Normally, registry entries are not case sensitive. However, in the case
	  of both of these entries, they are case sensitive. When adding these new
	  keys, be sure to match the case exactly as it is shown in Step 5.
	
	4. Ensure that the registry on the PDC has the following entries. If these
	  entries are missing, add them according to the instructions in Step 5. Look
	  for the entries at the following registry key:
	
	     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\LSA
	
	  If the PDC has NWLink installed, the entry should be:
	
	     NetWareClientSupport:REG_DWORD:0x1
	
	  If the PDC has TCP/IP installed, the entry should be:
	
	     TCPIPClientSupport:REG_DWORD:0x1
	
	
	  WARNING: Using Registry Editor incorrectly can cause serious problems that may
	  require you to reinstall Windows NT. Microsoft cannot guarantee that problems
	  resulting from the incorrect use of Registry Editor can be solved. Use
	  Registry Editor at your own risk.
	
	5. Add the registry values to the PDC because it is here that the Windows NT
	  password is changed. To add the values:
	
	  a. Start Registry Editor (Regedt32.exe).
	
	  b. Under the HKEY_LOCAL_MACHINE subtree, go to the following subkey:
	
	     SYSTEM\CurrentControlSet\Control\LSA
	
	  c. On the Edit menu, click Add Value.
	
	  d. If NWLink is installed on the PDC, type "NetWareClientSupport" (without
	     the quotation marks) under Field Type.
	
	  e. In the Data Type field, choose REG_DWORD, and click OK.
	
	  f. In the DWORD editor, in the Data field, type "1" (without the quotation
	     marks).
	
	  g. Click OK. The new value should appear as an entry.
	
	  h. Repeat steps a through f for TCPIPClientSupport if TCPIP is installed on
	     the PDC.
	
	  i. Restart the PDC for the changes to take effect.
	
	
	Additional query words: password change faq 8.0 8.01 8.02 8.03 8.04 8.5 9.0
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbOutlookSearch kbExchangeSearch kbExchangeClientSearch kbZNotKeyword kbZNotKeyword2 kbZNotKeyword3
	Version           : WINDOWS:4.0,5.0,8.0; :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
