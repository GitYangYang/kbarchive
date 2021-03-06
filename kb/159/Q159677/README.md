---
layout: page
title: "Q159677: Flight Simulator Err Msg: MMSystem263 &#91;MCI&#93; Device Not Connected"
permalink: /kb/159/Q159677/
---

## Q159677: Flight Simulator Err Msg: MMSystem263 &#91;MCI&#93; Device Not Connected

{% raw %}

	Article: Q159677
	Product(s): Microsoft Home Games
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbmm kbimu
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Flight Simulator for Windows 95, version 1.0 
	- Microsoft Flight Simulator 98 
	- Microsoft Flight Simulator 2000 
	- Microsoft Flight Simulator 2000 Professional Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start Flight Simulator 2000, Flight Simulator 98, or Flight Simulator
	for Windows 95, you may receive the following error message:
	
	  MMSystem263 [MCI] Device not connected.
	
	CAUSE
	=====
	
	This behavior can occur if the Motion Video Device on the computer is not
	configured properly.
	
	RESOLUTION
	==========
	
	To resolve this issue, remove and then reinstall the Motion Video Device. To do
	this:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Multimedia.
	
	3. Click the Advanced or Devices tab.
	
	4. Click the PLUS SIGN (+) next to Media Control Devices to expand the branch.
	
	5. Click Motion Video Device (Media Control), and then click Properties.
	
	6. Click Remove, and then click Yes.
	
	7. Click OK or Close until you return to Control Panel.
	
	8. Restart the computer.
	
	9. Click Start, point to Settings, and then click Control Panel.
	
	10. Double-click Add New Hardware, and then click Next. If you are using
	  Microsoft Windows 98, click Next again.
	
	11. When you are prompted to let Windows search for the hardware, click "No, I
	  want to select the hardware from a list".
	
	12. In the Hardware Types box, click "Sound, video and game controllers", and
	  then click Next.
	
	13. In the Manufacturers box, click Microsoft MCI.
	
	14. In the Models box, click Motion Video Device (Media Control), and then click
	  Next.
	
	15. Click Finish.
	
	16. Restart the computer.
	
	NOTE: If the Motion Video Device (Media Control) is not listed, you must follow
	steps 9 through 16 to install the device.
	
	To work around this issue, disable the Flight Simulator Intro movies when you
	start the game. To do this:
	
	1. Click Start, point to Find, and then click "Files or Folders".
	
	2. In the "Look in" box, click My Computer.
	
	3. In the Named box, type the appropriate following line for your version of
	  Flight Simulator, and then click Find Now.
	
	Flight Simulator 2000:
	
	  Fs2000.cfg
	
	Flight Simulator 98:
	
	  Fltsim98.cfg
	
	Flight Simulator for Windows 95:
	
	  Fltsim95.cfg
	
	4. In the list of found files, double-click your configuration file.
	
	5. In the "Choose the program you want to use" box, click Notepad, and then
	  click OK.
	
	6. Locate the [MAIN] section in the configuration file.
	
	7. Under the [MAIN] section, type the following line, and then press ENTER:
	
	  Showlogo=0
	
	8. On the File menu, click Exit. When you are prompted to save the changes,
	  click Yes.
	
	When you start Flight Simulator, the intro movies do not appear, and you do not
	receive the error message.
	
	MORE INFORMATION
	================
	
	For additional information about MCI error messages, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q136983 No Sound, MMSystem or MCI Errors in Windows 95
	
	
	Additional query words: 1.00 6.00 flightsim fs6 fs95 mmsystem263 logo avi opening hang startup MCI fs98 fs2k
	
	======================================================================
	Keywords          : kbenv kberrmsg kbmm kbimu 
	Technology        : _IKkbbogus kbGamesSearch kbFlightSimSearch kbFlightSim2000 kbFlightSim98 kbFlightSim95 kbSimSearch
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
