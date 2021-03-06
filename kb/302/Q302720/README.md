---
layout: page
title: "Q302720: Primary Account Cannot Be Deleted When Child Accounts Are Presen"
permalink: /kb/302/Q302720/
---

## Q302720: Primary Account Cannot Be Deleted When Child Accounts Are Presen

{% raw %}

	Article: Q302720
	Product(s): The Microsoft Network
	Version(s): 6.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network version 6.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You sign in to MSN Explorer 6.1 on a computer with one "account manager" account
	(an account associated with an MSN Internet Access subscriber) and one or more
	"child" accounts (non-paying accounts). You sign in using the user tile for the
	account manager. You click Help and Settings, click Accounts, and then click
	Remove Users. The Remove link for the primary account is not active, and this
	prevents you from deleting the account.
	
	CAUSE
	=====
	
	You cannot delete the primary account in MSN Explorer 6.1 until all child
	accounts have been deleted.
	
	RESOLUTION
	==========
	
	Delete all child accounts before attempting to delete the primary account.
	To delete all child accounts
	
	1. Using the account manager account, start MSN Explorer 6.1.
	
	2. In the upper-right corner, click Help and Settings.
	
	3. In the menu on the left, click Accounts, and then click Remove Users.
	  You should now see a list of all users on the machine, and the Remove link
	  next to the account manager account is not active.
	
	4. Click the Remove link next to any of the child accounts.
	
	5. Click OK, and then click OK again.
	  You will now be taken back to the list of accounts, minus the one that was
	  just removed.
	
	6. Repeat steps 4-5 for each child account on the machine.
	  After all of the child accounts have been removed, the Remove link next to the
	  account manager account will be active.
	
	7. Click the Remove link.
	
	8. Click OK, and then click OK again.
	  You will now be taken to the Welcome screen of MSN Explorer.
	
	Additional query words: kbimu; MSN Explorer
	
	======================================================================
	Keywords          :  
	Technology        : kbMSNSearch kbMSN610 kbMSNExplorer
	Version           : :6.1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
