---
layout: page
title: "Q231550: Err Msg: Microsoft MapPoint 2000 GB Was Previously Installed..."
permalink: /kb/231/Q231550/
---

## Q231550: Err Msg: Microsoft MapPoint 2000 GB Was Previously Installed...

{% raw %}

	Article: Q231550
	Product(s): Microsoft Automap
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsetup kbimu
	Last Modified: 14-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MapPoint 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to install Microsoft MapPoint 2000 United States (US), you may
	receive the following error message:
	
	  Microsoft MapPoint 2000 GB was previously installed on this system. You
	  cannot install Microsoft MapPoint 2000 without first removing Microsoft
	  MapPoint 2000 GB.
	
	CAUSE
	=====
	
	This behavior can occur if you manually remove Microsoft MapPoint 2000 Great
	Britain (GB) before you attempt to install MapPoint 2000 US.
	
	RESOLUTION
	==========
	
	To resolve this issue:
	
	1. Reinstall MapPoint 2000 GB.
	
	2. Click Start, point to Settings, and then click Control Panel.
	
	3. Double-click Add/Remove Programs.
	
	4. Click Microsoft MapPoint 2000 GB, and then click Add/Remove.
	
	5. Follow the instructions on the screen to remove MapPoint 2000 GB. If you are
	  prompted to restart your computer, do so.
	
	6. Click Start, point to Find, and then click "Files or Folders."
	
	7. In the Named box, type "Newmap.ptt" (without the quotation marks).
	
	8. In the "Look in" box, click My Computer, and then click Find Now.
	
	9. In the list of found files, right-click the Newmap.ptt file, and then click
	  Delete.
	
	10. When you are prompted to confirm the file deletion, click Yes.
	
	11. Install MapPoint 2000 US.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft MapPoint 2000.
	
	MORE INFORMATION
	================
	
	When you manually remove MapPoint 2000 GB, registry entries that only recognize
	MapPoint 2000 GB are not removed from the registry.
	
	Additional query words: mp2000 uninstall united kingdom uk europe
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsetup kbimu 
	Technology        : kbHomeProdSearch kbMapptSearch kbMapPoint2000
	Version           : WINDOWS:
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
