---
layout: page
title: "Q126398: Limits on OtherServers Parameter in SNA Server."
permalink: /kb/126/Q126398/
---

## Q126398: Limits on OtherServers Parameter in SNA Server.

{% raw %}

	Article: Q126398
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,2.11 SP1,3.0
	Operating System(s): 
	Keyword(s): kbenv kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1, 3.0, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The OtherServers option on SNA Server clients gives the client access to LUs
	through SNA Servers that are outside of the client's primary SNA Server domain.
	The number of servers that can be listed in the OtherServers parameter depends
	on the client's computer platform as follows:
	
	Platform     Maximum Number of Servers in OtherServers
	----------   -----------------------------------------
	Windows NT   No limit
	Windows 95   16
	Win3.x:      15 (or 256/<length of server name>)
	MS-DOS:      8
	
	MORE INFORMATION
	================
	
	The number of servers in the local domain may limit the number of OtherServers
	you can actually use. Local servers are added to the service table before
	OtherServers. The service table has 32 entries in Win3.x, 16 in DOS, 1024 in
	Windows 95 and 1024 in Windows NT. The sponsor naps and the local nap reserve
	one entry in the service table. Also, if any invokable APPC transaction programs
	(TP) are configured on an SNA Server client, each local TP reserves one service
	table entry.
	
	For additional information, refer to page 207, Appendix C, of the Microsoft SNA
	Server Reference Guide.
	
	Additional query words: ntprotocol prodsna
	
	======================================================================
	Keywords          : kbenv kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.0,2.1,2.11,2.11 SP1,3.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
