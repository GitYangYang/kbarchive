---
layout: page
title: "Q288238: Fix from Q275657 Causes Problems with HTML Admin"
permalink: /kb/288/Q288238/
---

## Q288238: Fix from Q275657 Causes Problems with HTML Admin

{% raw %}

	Article: Q288238
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you install the fix from Microsoft Knowledge Base article Q275657, the
	return address that is used after a password change becomes corrupted.
	
	CAUSE
	=====
	
	If you choose to change the password, a pop-up window displays the "The password
	is successfully changed" message, but the link to close this window is wrong.
	For example, the link appears as
	
	  http%3A//www.microsoft.com
	
	instead of:
	
	  http://www.microsoft.com
	
	WORKAROUND
	==========
	
	The password change functionality is working correctly; the problem lies in the
	return link. To work around this problem, click the Back button to return to the
	calling page.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Windows NT service pack that contains this fix.
	
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
	
	This fix is included with the fix in the following Microsoft Knowledge Base
	article:
	
	  Q287913 URL Protocol Contains "A" When You Are Redirected to Change Password
	  Page
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Internet Information Server 5.0.
	
	MORE INFORMATION
	================
	
	This problem has been observed in sites that use Microsoft Exchange Outlook Web
	Access.
	
	Additional query words: OWA
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
