---
layout: page
title: "Q169487: Access Violation in Mngcli.exe When You Close Server Manager"
permalink: /kb/169/Q169487/
---

## Q169487: Access Violation in Mngcli.exe When You Close Server Manager

{% raw %}

	Article: Q169487
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After you start SNA Server Manager, if you close Server Manager before the
	domain is fully opened (that is, while the hourglass is displaying before the
	configuration information appears), an access violation can occur in Mngcli.exe.
	An entry in <Ntroot>\Drwtsn32.log will be created as follows:
	
	  Application exception occurred:
	     App: mngcli.dbg (<process ID>)
	     Exception number: c0000005 (access violation)
	
	  [...]
	
	  function: EnterCriticalSection
	
	  FAULT ->77f4704a f0ff4204    lock   inc dword ptr [edx+0x4]
	  ds:0068e923=????????
	
	CAUSE
	=====
	
	Server Manager attempts to close the domain that was already closed.
	
	RESOLUTION
	==========
	
	To work around this problem:
	
	  Do not close Server Manager until the domain has been opened and the
	  configuration information is displayed.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 3.0 and 3.0
	Service Pack 1. This problem was corrected in the latest SNA Server version 3.0
	U.S. Service Pack. For information on obtaining this Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	When this problem occurs, the stack back trace may look like this:
	
	  *----> Stack Back Trace <----*
	
	  FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name
	  0111fd94 614812df 00000000 6149d3ec 6148dd0d 6149d3ec
	  kernel32!EnterCriticalSection
	  0111fda0 6148dd0d 6149d3ec 00000000 00000214 6149d36c snamanag!SyncRead
	  0111fdc0 61490656 6149d3ec 0111fde6 614906f0 00000000 snamanag!EnumList
	  0111fde4 0100df29 1f7fffff 002e1768 010071cb 1f7fffff
	  snamanag!SNADomainUnlock
	  0111fdf0 010071cb 1f7fffff 60210000 00000000 60983130
	     mngcli!DoCloseDomain
	  0111fe0c 01006dcc 002e14b0 00000040 00000003 010014f4
	  mngcli!CDomainProxy::Close
	  0111fe24 609843c1 0111fe44 0111fe8c 03d711ac 011203a0
	  mngcli!CDomainProxy::OnNotifySetting
	  0111fe50 60989887 011203a0 002e1660 77ea5848 6098126c
	  mngbase!CManage::OtherProcTerminated
	  0111fe8c 6098b220 0111fe9c 00000003 002e1440 00000002
	  mngbase!CAttachSink::OnUnknownAction
	  0111fea8 01009b15 602042b2 77f52f1c 0012febc 77fa1773
	  mngbase!CNotifyQueue::Dispatch
	  0111ffb8 77f46c2e 0012febc 602042b2 77f52f1c 0012febc
	     mngcli!DoAgentProxy
	  602042b2 000d8964 5e000000 5de58b5b ccccccc3 cccccccc
	  kernel32!BaseThreadStart
	
	With this hotfix applied, Server Manager checks to see whether the domain is
	already closed before attempting to close it.
	
	Additional query words: crash
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:3.0,3.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
