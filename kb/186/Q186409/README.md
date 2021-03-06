---
layout: page
title: "Q186409: SMS: Using Filters in Systems Management Server Administrator"
permalink: /kb/186/Q186409/
---

## Q186409: SMS: Using Filters in Systems Management Server Administrator

{% raw %}

	Article: Q186409
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbsmsAdmin smsadmin
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides step-by-step procedures to setup and remove filters using
	the Systems Management Server Administrator program. Systems Management Server
	has the ability to filter the Systems Management Server Administrator windows to
	include or exclude items that meet specified criteria in the view. An example of
	how to use this functionality is provided below.
	
	MORE INFORMATION
	================
	
	Note that filters can be set on any Systems Management Server Administrator
	Window. In this instance, you are using filters to prevent the display of System
	Jobs in the Jobs window.
	
	To set up a filter in the Systems Management Server Administrator program,
	perform the steps in the following example:
	
	1. On the File menu, click Open, and then select Jobs.
	
	2. On the View menu, click Filter.
	
	3. In the first list box, select Type.
	
	4. In the second list box, select Is Not Equal To.
	
	5. In the third box, type "System Job" (without the quotation marks).
	
	6. Click OK.
	
	The Jobs Window should be titled "Jobs (Filtered)" and will not show jobs where
	the type field is System Job, which effectively hides system jobs.
	
	To remove the filter, do the following:
	
	1. On the File menu, click Open, and then select Jobs.
	
	2. On the View menu, click Filter.
	
	3. In the first list box, scroll up and select No Filter, and then click OK.
	
	All jobs should now be displayed.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsmsAdmin smsadmin 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbhowto kbinfo
	
	=============================================================================
	

{% endraw %}
