---
layout: page
title: "Q224327: XCON: Inetinfo Stops with ASP Event 5 in CDO!EcDecompressData"
permalink: /kb/224/Q224327/
---

## Q224327: XCON: Inetinfo Stops with ASP Event 5 in CDO!EcDecompressData

{% raw %}

	Article: Q224327
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): EXC55SP3Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Inetinfo process may stop responding (crash) with Active Server Pages (ASP)
	Event ID 5. The text of the error message is:
	
	  Error: Unexpected error
	
	CAUSE
	=====
	
	If correct symbols are installed, the call stack looks like the following:
	
	FramePtr  RetAddr   Param1   Param2   Param3   Function Name
	045ff4fc  6f0ae317  10d01408 000007de 10cb9008 CDO!EcDecompressData+0x1b8
	045ff518  6f0d3782  00000000 10cb9008 0000066f CDO!EcHandleCompression+0x157
	045ff560  6f0b301a  0000067f 00046c00 045ff584 CDO!TFILE::EcRead+0x1c2({...})
	045ff584  6f0b316a  00000000 045ff5b0 045ff5aa CDO!IDXND::EcInstallChild+0x4a
	045ff5bc  6f0b5d0a  045ff614 05bc97f8 045ff624 CDO!IDXND::EcSearchObject+0x8a
	045ff5ec  6f0b7572  00000000 045ff614 05bc97f8 CDO!IDXRT::EcSearchTree+0x5a
	045ff618  6f0b9144  05bc97f8 00000000 00000000 CDO!IDXRT::EcLoadObj+0x62
	045ff660  6f0b902b  00000000 00000001 045ff6cc CDO!IDXRT::EcGetRestrictedRows+0x114
	045ff678  6f0bf7e1  05bc97b8 00000001 045ff6cc CDO!IDXRT::EcGetRows+0x1b
	045ff6d4  6f0bb8c7  00000000 05bc9780 00000000 CDO!BUSYMT::EcNextBusyItem+0x121
	045ff774  6f0bb7eb  00000000 00000000 17cbe140 CDO!BUSYMT::EcGetNextInstance+0x77
	045ff79c  6f0baedd  00000000 0000000a 7fffffff CDO!BUSYMT::EcReloadTable+0x36b
	045ff7bc  6f08e502  7fffffff 045ff7e8 00000000 CDO!BUSYMT::EcGetRows+0xcd
	045ff800  6fa9acd1  0d989868 7fffffff 00000000 CDO!CMTableOnSTable::QueryRows+0x92
	045ff828  01c265a1  00000000 00000000 17e426a8 MAPI32!HrQueryAllRows+0x131
	045ff894  01c25b50  045ff8d0 00000001 0000000b CDOHTML!CCalendarView::HrReadAppointments+0x1d1({...})
	045ff9ac  766f6094  17e425f8 045f400c 045ffb5c CDOHTML!CCalendarView::RenderEvents+0x1d0({...}, {...})
	045ffa78  01c1e282  05b70554 17e425f8 00000140 0x766f6094
	045ffaa4  01c40b77  17e425f8 00000140 6b641458 CDOHTML!CComTypeInfoHolder::Invoke+0x52({...})
	045ffacc  6b60d1e1  17e425f8 00000140 6b641458 CDOHTML!Invoke+0x37({...})
	00000800  00000000  00000000 00000000 00000000 0x6b60d1e1
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: CDO
	
	+------------------------+
	| File name | Version    | 
	+------------------------+
	| Cdo.dll   | 5.5.2579.0 | 
	+------------------------+
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5 service pack 3. This problem was first corrected in Exchange Server
	5.5 Service Pack 3.
	
	Additional query words: cdo calender inetinfo asp 5
	
	======================================================================
	Keywords          : EXC55SP3Fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
