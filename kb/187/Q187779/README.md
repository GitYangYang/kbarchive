---
layout: page
title: "Q187779: XADM: Error: Warning &#91;30&#93; Message Contains Duplicate Email Addre"
permalink: /kb/187/Q187779/
---

## Q187779: XADM: Error: Warning &#91;30&#93; Message Contains Duplicate Email Addre

{% raw %}

	Article: Q187779
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): exc4 exc5 exc55
	Last Modified: 22-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After a new Exchange Server computer has been added to an Exchange Server site,
	that is a requestor in directory synchronization (dirsync) with a Microsoft Mail
	3.x postoffice (PO), the following warnings may appear in the Dirsync log:
	
	   Warning [154]Non delivery report
	   Warning [30] 154 Message contains duplicate email address. Mail item
	   was not delivered to(requestor name)
	
	Address lists updates will not be propagated to the Exchange Server site, and no
	errors or warnings will show up in the Event Log for the Exchange requestor.
	
	CAUSE
	=====
	
	The new Exchange Server computer has been given the Microsoft Mail address
	"SHADOWNET\SHADOWPO\SYSTEM1" under the Directory Synchronization tab as the
	Requestor server. Consequently, the errors occur and dirsync stops functioning.
	
	Usually, when a new server is added to the site, directory replication checks for
	other MS Mail connectors and if it finds any, it automatically increments the MS
	Mail address in sequential order. For example, if a fourth Exchange Server
	computer is added to a site with an MS Mail connector, as a dirsync requestor,
	it will look for the connector during directory replication, and then assign it
	the address SHADOWNET\SHADOWPO\SYSTEM4.
	
	WORKAROUND
	==========
	
	On the Directory Synchronization Properties page, highlight the new server and
	edit the Microsoft Mail e-mail address.
	
	MORE INFORMATION
	================
	
	For additional information on how the Exchange Server Directory Synchronization
	address can be changed, please see the following Microsoft Knowledge Base
	article:
	
	  Q150828 XFOR: Dirsync Role/Number of Servers can Change DXA Addresses
	
	Additional query words: dirsync new address error 30 thirty
	
	======================================================================
	Keywords          : exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
