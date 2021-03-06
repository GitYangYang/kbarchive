---
layout: page
title: "Q239531: Streets 98 Err Msg: General Protection Fault in Module &lt;Unknown&gt;"
permalink: /kb/239/Q239531/
---

## Q239531: Streets 98 Err Msg: General Protection Fault in Module &lt;Unknown&gt;

{% raw %}

	Article: Q239531
	Product(s): Microsoft Automap
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kberrmsg kbprint kbimu
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Expedia Streets 98 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to print a map from Microsoft Expedia Streets 98, you may
	receive the following error message:
	
	  Autmap6 caused a general protection fault in module <unknown>.
	
	CAUSE
	=====
	
	This behavior can occur if one of the following video adapters is installed in
	your computer.
	
	- Diamond Viper V550
	- STB nVidia ZXV, 8 MB AGP
	- STB Velocity 128
	
	RESOLUTION
	==========
	
	To work around this issue, use either of the following methods:
	
	Configure Your Computer to Use a High Color (16 bit) Palette
	------------------------------------------------------------
	
	To configure your computer to use a High Color (16 bit) palette:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Display.
	
	3. Click the Settings tab.
	
	4. In the Color Palette or Colors box, click High Color (16 bit).
	
	5. Click OK. If you are prompted to restart your computer, do so.
	
	Reduce Graphics Hardware Acceleration
	-------------------------------------
	
	To reduce graphics hardware acceleration:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click System.
	
	3. On the Performance tab, click Graphics.
	
	4. Move the Hardware Acceleration slider until it is one notch to the right of
	  None (the Basic acceleration setting).
	
	5. Click OK, and then click Close.
	
	6. When you are prompted to restart your computer, click Yes.
	
	NOTE: If you encounter any problems after you reduce graphics hardware
	acceleration, follow these steps to restore graphics hardware acceleration to
	the original setting:
	
	a. Restart Windows in Safe mode. To do so, follow the appropriate steps for your
	  operating system.
	
	  Microsoft Windows 95:
	
	  Restart your computer. When you see the "Starting Windows 95" message, press
	  the F8 key, and then choose Safe Mode from the Startup menu.
	
	  Microsoft Windows 98:
	
	  Restart your computer, press and hold down the CTRL key after your computer
	  completes the Power On Self Test (POST), and then choose Safe Mode from the
	  Startup menu.
	
	b. When Windows starts in Safe mode, click OK.
	
	c. Repeat steps 1 through 6, but in step 4 move the Hardware Acceleration slider
	  back to its original position.
	
	MORE INFORMATION
	================
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: multi multi-media media mm auto-map amap
	
	======================================================================
	Keywords          : kberrmsg kbprint kbimu 
	Technology        : kbHomeProdSearch kbExpediaSearch
	Version           : WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
