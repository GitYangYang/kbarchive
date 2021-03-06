---
layout: page
title: "Q233400: XGEN: Using Windows2000 Encrypted File System to Encrypt Mdbdata"
permalink: /kb/233/Q233400/
---

## Q233400: XGEN: Using Windows2000 Encrypted File System to Encrypt Mdbdata

{% raw %}

	Article: Q233400
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5 SP3
	Operating System(s): 
	Keyword(s): exc55sp3
	Last Modified: 21-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP3 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you want to encrypt the Mdbdata folder with the Windows 2000 Encrypted File
	system, you need to be logged on as the Exchange Server service account.
	
	MORE INFORMATION
	================
	
	You must use the Exchange Server service account to encrypt the Mdbdata folder
	or the information store will not start. You must use the service account
	because this is the account which actually accesses the files within the Mdbdata
	folder. Users actually interface with the Information Store Service to access
	the Priv.edb, Pub.edb, and other files within the Mdbdata directory. The
	Information Store Service uses the security context of the service account to
	access the files.
	
	You may notice that the Information Store Service starts more slowly than usual
	after you apply the encryption because the files are being decrypted while the
	Information Store Service starts. After the files are decrypted, they remain
	decrypted as long as they are in use by the information store.
	
	If you get the following error message while starting the information store, it
	means that the file encryption attribute was not set using the service account.
	
	  Windows could not start the Microsoft Exchange Information Store on Local
	  Computer. For information, review the System Event Log. If this is a
	  non-Microsoft service, contact the service vendor, and refer to
	  service-specific error code -1032
	
	You may also see the following errors in the application log when you try to
	start the Information Store Service.
	
	  Event ID 145 - MSExchangeIS((1856)) could not access the file called
	  Exchsrvr\Mdbdata\Edb.chk
	
	  Event ID 1120 - MSExchangeIS((1856)) could not access the file called
	  Exchsrvr\Mdbdata\Edb.log
	
	  Event ID 5000 - Unable to initialize the Microsoft Exchange Information Store
	  error0xfffffbfb
	
	  Event ID 1005 - Unexpected error "0xc004000-The Microsoft Exchange Server
	  computer is not available. Either there are network problems or the Microsoft
	  Exchange Server computer is down for maintenance. Microsoft Exchange Server
	  Store ID no:8004011d-0526-00000000" occurred.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55sp3 
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP3
	Version           : winnt:5.5 SP3
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
