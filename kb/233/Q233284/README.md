---
layout: page
title: "Q233284: XADM: Event Service Causes Unwanted Public Folder Replication"
permalink: /kb/233/Q233284/
---

## Q233284: XADM: Event Service Causes Unwanted Public Folder Replication

{% raw %}

	Article: Q233284
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55 EXC55SP3Fix
	Last Modified: 30-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Scenario:
	
	You perform a custom installation of two Microsoft Exchange Server 5.5 computers
	in two different sites with no event service, for example, ServerA in SiteA,
	ServerB in SiteB. You set up directory replication with an X.400 Connector
	between SiteA and SiteB. Then, you create a public folder on ServerA/SiteA and
	replicate it to ServerB/SiteB.
	
	Problem:
	
	When you install Microsoft Exchange Event Service on ServerA/SiteA, the Exchange
	Server Administrator program shows the replica of the system folder
	EventsRoot\EventConfig_ServerA for ServerA/SiteB to ServerB/SiteB.
	
	CAUSE
	=====
	
	This behavior is caused by the fact that the parent EventsRoot folder is treated
	"specially" by the information store. If you start the Exchange Server
	Administrator program on a brand new server and site and try to view this
	special folder before replication from other servers and sites has occurred, a
	new (local) replica of the parent EventsRoot folder will be added. Over time,
	this parent folder may have a lot of servers in its replica list. Whenever a new
	child EventConfig_XXX folder is created, it automatically inherits this replica
	list.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Microsoft Exchange Event Service
	
	+--------------------------+
	| File name  | Version     | 
	+--------------------------+
	| Events.exe | 5.5.00.2628 | 
	+--------------------------+
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 3.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 EXC55SP3Fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
