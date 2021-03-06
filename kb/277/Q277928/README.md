---
layout: page
title: "Q277928: Snaservr.exe Access Violation in Functions S1PPIUSN &amp; S1PPSTAD"
permalink: /kb/277/Q277928/
---

## Q277928: Snaservr.exe Access Violation in Functions S1PPIUSN &amp; S1PPSTAD

{% raw %}

	Article: Q277928
	Product(s): Microsoft SNA Server
	Version(s): 4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Operating System(s): 
	Keyword(s): sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 kbSNA400sp4fix kbSNA400PreSP4fix
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The SNA Server service (Snaservr.exe) may experience an Access Violation (AV) in
	the S1ppiusn or S1ppstad function when an application such as Performance
	Monitor (PerfMon) is querying the SNA Server performance monitor counters. Other
	applications may also query performance monitor counters, including Compaq's
	Insight Manager.
	
	If Drwtsn32.exe is configured as the default debugger on the SNA Server/Host
	Integration Server (HIS) 2000 system, information similar to the following may
	be appended to the Drwtsn32.log:
	
	  Application exception occurred:
	          App: exe\snaservr.dbg (pid=236)
	          When: 7/26/1999 @ 13:55:26.985
	          Exception number: c0000005 (access violation)
	
	  [...]
	  State Dump for Thread Id 0xef
	
	  eax=00252200 ebx=00000100 ecx=00000555 edx=00000105 esi=00000100 edi=0025222c
	  eip=010553e3 esp=00bcff10 ebp=00000105 iopl=0         nv up ei pl nz na pe nc
	  cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
	
	  function: s1ppiusn
	          010553c0 83ec10           sub     esp,0x10
	          010553c3 0fbf0582491801                                      ds:01184982=01c7
	                                    movsx   eax,word ptr [sncurrnt (01184982)]
	          010553ca 53               push    ebx
	          010553cb 55               push    ebp
	          010553cc 8d0440           lea     eax,[eax+eax*2]        ds:00252200=00000007
	          010553cf 56               push    esi
	          010553d0 57               push    edi
	          010553d1 0fbf2c85de4e1801                                    ds:00252200=0007
	                              movsx ebp,word ptr [buffer_shortage+0x2 (01184ede)+eax*4]
	          010553d9 8b04ad7cb71701                                  ds:00000105=????????
	                                    mov     eax,[s1seccb+0x1d8bc (0117b77c)+ebp*4]
	          010553e0 8b702c           mov     esi,[eax+0x2c]         ds:016c0c06=00000000
	  FAULT ->010553e3 8b4e04           mov     ecx,[esi+0x4]          ds:0146eb06=????????
	          010553e6 c744241400000000 mov   dword ptr [esp+0x14],0x0 ss:0203e917=????????
	
	  Application exception occurred:
	          App: exe\snaservr.dbg (pid=360)
	          When: 7/26/1999 @ 13:28:47.8
	          Exception number: c0000005 (access violation)
	
	  [...]
	
	  State Dump for Thread Id 0xe6
	
	  eax=00000000 ebx=00000002 ecx=02440000 edx=00131201 esi=00bcff54 edi=00252200
	  eip=01054d99 esp=00bcff24 ebp=00000104 iopl=0         nv up ei pl zr ac po nc
	  cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000256
	
	  function: s1ppstad
	          01054d82 eb09             jmp     s1ppstad+0x6d (01054d8d)
	          01054d84 8b4910           mov     ecx,[ecx+0x10]         ds:038aea06=????????
	          01054d87 8a5008           mov     dl,[eax+0x8]                 ds:0146ea06=??
	          01054d8a 8a5809           mov     bl,[eax+0x9]                 ds:0146ea06=??
	          01054d8d 32c0             xor     al,al
	          01054d8f 85c9             test    ecx,ecx
	          01054d91 7416             jz      s1ppstad+0x89 (01054da9)
	          01054d93 84c0             test    al,al
	          01054d95 7516             jnz     s1ppstad+0x8d (01054dad)
	          01054d97 33c0             xor     eax,eax
	  FAULT ->01054d99 385104           cmp     [ecx+0x4],dl                 ds:038aea06=??
	          01054d9c 0f94c0           sete    al
	
	CAUSE
	=====
	
	A problem in the SNA Server performance monitoring functions can cause invalid
	output to be returned to the performance monitoring application (for example,
	PerfMon) or to the Access Violations described here. This problem occurs only
	under certain conditions, and therefore the problem may occur only rarely and
	may be difficult to reproduce.
	
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for SNA Server 4.0. For
	additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q215838 How to Obtain the Latest SNA Server Version 4.0 Service Pack
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server versions
	4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, and Microsoft Host Integration Server 2000.
	
	This problem was first corrected in SNA Server 4.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: sp1 sp2 sp3 service pack
	
	======================================================================
	Keywords          : sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 kbSNA400sp4fix kbSNA400PreSP4fix 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3
	Version           : :4.0,4.0 SP1,4.0 SP2,4.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
