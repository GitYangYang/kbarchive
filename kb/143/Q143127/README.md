---
layout: page
title: "Q143127: BOOTP Relay Agents Fail Using Multiple Logical IP Subnets"
permalink: /kb/143/Q143127/
---

## Q143127: BOOTP Relay Agents Fail Using Multiple Logical IP Subnets

{% raw %}

	Article: Q143127
	Product(s): Microsoft Windows NT
	Version(s): 3.11 3.5 3.51 95 4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft LAN Manager, version 2.2c 
	- Microsoft Windows for Workgroups version 3.11 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	BOOTP relay agents are not able to successfully service all DHCP client
	computers from a LAN segment using multiple logical IP subnets. Only one of the
	logical IP subnets is able to obtain DHCP IP addresses for its DHCP client
	computers.
	
	For additional information on DHCP with multiple logical IP subnets when you are
	not using relay agents, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q124026
	  TITLE : Requests Fail on Logically Multihomed Server (Single NIC)
	
	MORE INFORMATION
	================
	
	A router implemented as a BOOTP relay agent must insert its IP address in the
	gateway IP address (giaddr) field of the DHCP Discover packet. A DHCP server
	uses the giaddr field to determine the subnet that sent the request for IP
	addresses and which IP addresses to offer. If the giaddr field is blank, the
	DHCP server assumes that the request is from the local subnet.
	
	The following is an excerpt from RFC 1542:
	
	  If the relay agent does decide to relay the request, it MUST examine the
	  "giaddr" ("gateway" IP address) field. If this field is zero, the relay agent
	  MUST fill this field with the IP address of the interface on which the
	  request was received. If the interface has more than one IP address logically
	  associated with it, the relay agent SHOULD choose one IP address associated
	  with that interface and use it consistently for all BOOTP messages it relays.
	
	Because only one address is used in the giaddr field by the relay agent, only one
	of the logical subnets is serviced through DHCP.
	
	Additional query words: prodnt 3.5 3.51 4.0
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbAudDeveloper kbWin95search kbLanManSearch kbWFWSearch kbZNotKeyword3 kbWFW311 kbLanMan220c
	Version           : 3.11 3.5 3.51 95 4.0
	
	=============================================================================
	

{% endraw %}
