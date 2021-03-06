---
layout: page
title: "Q286168: Application Exception in Snalink!UpdateDLSData"
permalink: /kb/286/Q286168/
---

## Q286168: Application Exception in Snalink!UpdateDLSData

{% raw %}

	Article: Q286168
	Product(s): Microsoft SNA Server
	Version(s): 3.0 (all SP),4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Operating System(s): 
	Keyword(s): kbDSupport kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	SNA Server or Host Integration Server 2000 systems being used to distribute DLC
	802.2 link services for use by branch SNA Servers and/or Host Integration 2000
	servers in a Distributed Link Service (DLS) environment may experience an
	application exception in Snalink!UpdateDLSData.
	
	NOTE: The problem only occurs when a DLS connection terminates unexpectedly.
	Therefore, the Application Event log may contain events normally associated with
	connection outages prior to the application exception. Common connection outage
	events logged by SNA Server/HIS 2000 include the following events: 23, 227, 226.
	
	CAUSE
	=====
	
	The application exception occurs when a NULL message pointer is passed into the
	UpdateDLSData function.
	
	RESOLUTION
	==========
	
	SNA Server 4.0
	--------------
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft SNA Server version 4.0 service pack that contains this
	fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	+-----------------------------------+
	| File name  | Date       | Time    | 
	+-----------------------------------+
	| Snadlc.dll | 01/26/2001 | 09:13AM | 
	+-----------------------------------+
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	Host Integration Server 2000
	----------------------------
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Host Integration Server 2000 service pack that contains
	this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	+-----------------------------------+
	| File name  | Date       | Time    | 
	+-----------------------------------+
	| Snadlc.dll | 01/26/2001 | 09:13AM | 
	+-----------------------------------+
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server versions
	3.0 (all Service Packs [SPs]), 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, and Host
	Integration Server 2000.
	
	MORE INFORMATION
	================
	
	If DRWTSN32.exe is configured as the default debugger, information similar to
	the following is added to the DRWTSN32.LOG when this application exception
	occurs:
	
	Application exception occurred:
	       App: exe\snalink.dbg (pid=89)
	       When: 12/5/2000 @ 19:8:42.58
	       Exception number: c0000005 (access violation)
	
	  [data omitted...]
	
	       6338917d 7fec             jg      UpdateDLSData+0x8b (6338916b)
	       6338917f a17c1a3963   mov eax,[DlsData+0x344 (63391a7c)] ds:63391a7c=63391a80
	       63389184 6840173963       push    0x63391740
	       63389189 50               push    eax
	       6338918a 6849173963       push    0x63391749
	       6338918f ffd3             call    ebx
	       63389191 83c40c           add     esp,0xc
	       63389194 c7053817396300000000                            ds:63391738=00000000
	                                 mov     dword ptr [DlsData (63391738)],0x0
	       6338919e 8bb42420010000   mov     esi,[esp+0x120]        ss:00baff0c=63387d83
	       633891a5 6849183963       push    0x63391849
	FAULT ->633891aa 660fb64e0a       movzx   cx,byte ptr [esi+0xa]        ds:0161ea08=??
	       633891af 51               push    ecx
	       633891b0 e84f350000       call    GetClientWorkstationName (6338c704)
	       633891b5 85c0             test    eax,eax
	       633891b7 0f84cd010000     je      UpdateDLSData+0x2aa (6338938a)
	       633891bd 8d542414         lea     edx,[esp+0x14]         ss:021ce7f3=????????
	       633891c1 52               push    edx
	       633891c2 6a03             push    0x3
	       633891c4 6a00             push    0x0
	       633891c6 6849173963       push    0x63391749
	       633891cb 6802000080       push    0x80000002
	       633891d0 ff1500103863                                    ds:63381000=77dd992e
	                                 call    dword ptr [_imp__RegOpenKeyExA (63381000)]
	
	In addition, an event similar to the following will be logged in the Application
	Event Log:
	
	  Event ID: 624
	  Source: SNA Server
	  Description: Creating dump file D:\sna\traces\snadump.log for snalink.exe
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDSupport kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 kbhis2000 kbsna400sp4 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ400SP4 kbSNAServ300SP2 kbSNAServ300SP4
	Version           : :3.0 (all SP),4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
