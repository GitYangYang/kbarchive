---
layout: page
title: "Q138897: MS Fax Does Not Recognize the &quot;&#36;&quot; Calling Card Dialing Rule"
permalink: /kb/138/Q138897/
---

## Q138897: MS Fax Does Not Recognize the &quot;&#36;&quot; Calling Card Dialing Rule

{% raw %}

	Article: Q138897
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): kbtool win95 msnetwork
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to send a fax using Microsoft Fax configured to use the "Wait for
	calling card prompt (bong)" or "$" dialing rule, the calling card and PIN
	numbers may not be dialed.
	
	CAUSE
	=====
	
	The "$" calling card dialing rule instructs the modem to wait and listen for a
	tone (or "bong") generated by the phone company to activate the dialing of the
	calling card and PIN numbers.
	
	Microsoft Fax does not properly handle the "$" rule unless your modem is
	specifically designed to handle the "bong."
	
	
	RESOLUTION
	==========
	
	To cause the calling card and PIN numbers to be dialed when you send a fax with
	Microsoft Fax, follow these steps:
	
	1. In Control Panel, double-click the Modems icon.
	
	2. Click Dialing Properties.
	
	3. Click Change to edit the properties for the calling card.
	
	4. Click New, type a name for the custom calling card, and then click OK.
	
	5. Click Advanced.
	
	6. Click Copy From, click your calling card, and then click OK.
	
	7. Edit the dialing rules. Replace all instances of "$" with four commas. You
	  can adjust the number of commas as is appropriate for your modem.
	
	8. Click OK or Close until you return to Control Panel.
	
	MORE INFORMATION
	================
	
	The modem driver normally translates the "$" into a series of commas for modems
	that are not designed to handle the "bong," but Microsoft Fax bypasses the
	portion of the modem driver that performs this translation.
	
	======================================================================
	Keywords          : kbtool win95 msnetwork 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
