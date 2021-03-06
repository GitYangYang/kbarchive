---
layout: page
title: "Q138390: Cannot Find API getnamebyaddr Referred to in TN3270 Event 203"
permalink: /kb/138/Q138390/
---

## Q138390: Cannot Find API getnamebyaddr Referred to in TN3270 Event 203

{% raw %}

	Article: Q138390
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11
	Operating System(s): 
	Keyword(s): kbinterop kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 2.11 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	You cannot find the getnamebyaddr application programming interface (API) after
	you configure TN3270 Server to resolve IP addresses to NetBIOS names and this
	process fails causing the following event in the system log:
	
	  Event 203: TN3270 server
	
	  Description:
	  Windows Sockets API call getnamebyaddr(xxx.xxx.xxx.xxx) failed in
	  function TCPSessionInitialize with return code WSANO_DATA.
	
	  EXPLANATION
	  An unexpected error was encountered on a Windows Sockets API call.
	
	  ACTION
	  Record message and contact technical support.
	
	NOTE: xxx.xxx.xxx.xxx in the description above represents the IP address.
	
	CAUSE
	=====
	
	The API getnamebyaddr does not exist. Instead, Event 203 should refer to the API
	call gethostbyaddr.
	
	RESOLUTION
	==========
	
	
	WORKAROUND
	==========
	
	To work around this problem, evaluate the problem as if the API call
	gethostbyaddr is referenced in Event 203.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 2.11. This
	problem was corrected in the latest Microsoft SNA Server 2.11 U.S. Service Pack.
	For information on obtaining the service pack, query on the following word in
	the Microsoft Knowledge Base (without the spaces):
	
	  SERVPACK
	
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          : kbinterop kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ211
	Version           : WINDOWS:2.11
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
