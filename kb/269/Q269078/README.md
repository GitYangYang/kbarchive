---
layout: page
title: "Q269078: Domain Names Are Not Displayed in the Accounting Log"
permalink: /kb/269/Q269078/
---

## Q269078: Domain Names Are Not Displayed in the Accounting Log

{% raw %}

	Article: Q269078
	Product(s): Microsoft Windows NT
	Version(s): 4.0 SP6,4.0 SP6a
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 4.0 SP6, 4.0 SP6a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the Routing and Remote Access Service (RRAS) update and you
	authenticate against a Remote Authentication Dial-in User Service (RADIUS)
	server, even though you have set the DoNotStripDomainName registry setting to
	log on to multiple account domains, the domain names are not displayed in the
	accounting log.
	
	CAUSE
	=====
	
	This issue occurs because information about a user's logon domain is only
	retained when the information is returned from the authentication server. This
	information is not returned from the authentication server when you are using
	Password Authentication Protocol (PAP) as the authentication protocol.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Windows NT 4.0 service pack that contains this fix.
	
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
	
	Date      Time   Version    Size    File name   
	------------------------------------------------ 
	19/12/00  14:42  4.1.1.100   9,488  Rascbcp.dll
	19/12/00  14:42  4.1.1.100  33,552  Raschap.dll
	19/12/00  14:42  4.1.1.100  12,048  Raspap.dll
	19/12/00  14:41  4.1.1.100  60,688  Raspppen.dll
	19/12/00  14:42  4.1.1.100  14,608  Rasspap.dll
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	When this issue occurs, you are either unable to locate the users or you are not
	able to differentiate between users with the same logon name.
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q230014 RRAS Does Not Report Domain Name for Users in Accounting Packets
	
	Additional query words:
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400sp6 kbWinNTS400search
	Version           : :4.0 SP6,4.0 SP6a
	Hardware          : ALPHA x86
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
