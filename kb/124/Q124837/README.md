---
layout: page
title: "Q124837: Connecting to a Remote Network Monitor Agent Across a Router"
permalink: /kb/124/Q124837/
---

## Q124837: Connecting to a Remote Network Monitor Agent Across a Router

{% raw %}

	Article: Q124837
	Product(s): Microsoft Systems Management Server
	Version(s): 1.0,1.1,1.2,2.0,2.0 SP1,2.0 SP2,4.0
	Operating System(s): 
	Keyword(s): smsnetmon
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2, 2.0, 2.0 SP1, 2.0 SP2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Network Monitor can capture traffic on another subnet by connecting to a system
	that is running the Remote Agent software on that subnet. The Network Monitor
	Agent software is included with both Windows NT Workstation and Windows NT
	Server. In Network Monitor, when you click Networks on the Capture menu, Remote
	is one of the options. Provide the Agent's computer name (with or without "\\")
	to connect to it.
	
	For Network Monitor to connect to a Remote Agent across a router, the Remote
	Agent's computer name must be resolved. If the name cannot be resolved, you
	receive the following error message:
	
	  Failure connecting to <computer name of Agent>
	
	MORE INFORMATION
	================
	
	The Remote Agent registers a NetBIOS name which is 16 characters long. It
	consists of the computer name followed by 0xBE (extended characters). For
	example, a machine named "HITME" would be registered as
	"HITME\0xBE\0xBE\0xBE..."
	
	Use the following steps to connect to the agent across a router:
	
	1. Ensure that the Manager and the Remote Agent systems have a routable protocol
	  such as TCP/IP or NWLINK installed.
	
	2. Install the Network Monitor Agent software on the remote computer.
	
	3. Start the Network Monitor Agent Service by doing one of the following:
	
	  At the command prompt, type the following command:
	
	  net start nmagent
	
	  -or-
	
	  Double-click the Services icon in Control Panel, click Network Monitor Agent
	  in the Service list, and then click Start.
	
	4. If TCP/IP is the protocol that is used, then there are two ways to resolve a
	  NetBIOS name to an IP address. If both the management station and the remote
	  agent are using Microsoft Windows Internet Naming Service (WINS) then the
	  name will be resolved by WINS and WINS locates the Agent. If not, then the
	  Lmhosts file on the management station must contain a special entry for the
	  remote agent.
	
	  If TCP/IP is used and WINS is not available, add the Agent's name in the
	  Lmhosts file. Non-printing (extended) characters can be added by using \0xnn
	  format where nn represents the ASCII code for the character.
	
	  Following are some examples from an Lmhosts file.
	
	  130.1.2.3  "MYAGENT\0xBE\0xBE\0xBE\0xBE\0xBE\0xBE\0xBE\0xBE\0xBE"   #PRE
	  130.2.3.4  "REMOTEAGENT\0xBE\0xBE\0xBE\0xBE\0xBE"                   #PRE
	  130.3.4.5  "SEATTLESERVER\0xBE\0xBE\0xBE"                           #PRE
	
	  NOTE: Capital letters must be used for the agent name, the agent name must
	  consist of 16 characters surrounded by quotation marks, and #PRE must end
	  each entry.
	
	5. The NBTSTAT command can be used to flush and reload the LMHOSTS cache after
	  modifying the Lmhosts file. To reload the cache, type the following command
	  at a command prompt:
	
	  nbtstat -R
	
	  Note that the -R is case sensitive and must be uppercase.
	
	  To view the cache, type
	
	  nbtstat -c
	
	  After the cache has been updated, you should be able to connect to the remote
	  agent.
	
	6. If NWLINK protocol is used, NameQuery should succeed because most routers are
	  configured to forward broadcasts (packet type 20).
	
	
	Additional query words: prodsms Bloodhound Netmon BH
	
	======================================================================
	Keywords          : smsnetmon 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120 kbSMS200 kbSMS200SP1 kbSMS200SP2
	Version           : :1.0,1.1,1.2,2.0,2.0 SP1,2.0 SP2,4.0
	
	=============================================================================
	

{% endraw %}
