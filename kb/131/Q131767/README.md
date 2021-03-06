---
layout: page
title: "Q131767: Flight Simulator Err Msg: Unable to Lock XMS Memory"
permalink: /kb/131/Q131767/
---

## Q131767: Flight Simulator Err Msg: Unable to Lock XMS Memory

{% raw %}

	Article: Q131767
	Product(s): Microsoft Home Games
	Version(s): 5.0,5.1
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsetup kbimu
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Flight Simulator for MS-DOS, versions 5.0, 5.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start Microsoft Flight Simulator, you receive the following error
	message:
	
	  Unable to lock XMS memory
	
	CAUSE
	=====
	
	Flight Simulator tries to lock XMS memory. Windows does not allow an application
	to lock XMS memory.
	
	RESOLUTION
	==========
	
	To resolve this error message, set the Use XMS Memory option in Flight Simulator
	to No, as follows:
	
	Windows 95/98
	-------------
	
	There are three potential solutions to this problem in Windows 95/98. The
	solutions are listed below in order of preference.
	
	Option 1:
	
	1. Open your Flight Simulator 5.1 folder.
	
	2. Double-click Setup.com. Follow the Setup steps.
	
	3. When you reach the Sound Setup option, make sure the Use XMS Memory option is
	  set to No.
	
	4. Complete Setup and restart Flight Simulator.
	
	Option 2:
	
	1. Open the Flight Simulator 5.1 folder.
	
	2. Double-click Fs5.ini to open the Fs5.ini file in Notepad. (If Fs5.ini does
	  not automatically open in Notepad when you double-click Fs5.ini, choose
	  Notepad from the Windows 95/98 "Open With" dialog box.)
	
	3. In Fs5.ini, locate the line:
	
	  SOUND_XMS=001
	
	  -or-
	
	  SOUND_XMS=1
	
	4. Change the line to:
	
	  SOUND_XMS=000
	
	5. Save the changes and restart Flight Simulator.
	
	Option 3:
	
	1. Open the Flight Simulator 5.1 folder.
	
	2. With the right mouse button, click Fs5.com.
	
	3. Click Properties.
	
	4. From the Fs5.com Properties screen, click the Memory tab.
	
	5. On the Memory tab, set the Extended Memory option to Auto.
	
	6. Restart Flight Simulator.
	
	Windows 3.x
	-----------
	
	1. If you are using Windows 3.x, exit Windows, and from the Flight Simulator
	  directory, type the following and press ENTER:
	
	  setup
	
	2. Follow the Setup steps. When you reach the Sound Setup option, change the Use
	  XMS Memory option to No.
	
	3. Complete Setup and restart Flight Simulator.
	
	EDITING FS5.INI
	---------------
	
	If Flight Simulator does not allow you to use the steps above to physically
	change the XMS setting, edit your Fs5.ini file as follows:
	
	1. Find the line
	
	  SOUND_XMS=001
	
	  -or-
	
	  SOUND_XMS=1
	
	2. Change the line to:
	
	  SOUND_XMS=000
	
	MORE INFORMATION
	================
	
	Flight Simulator should now run without problems. If you continue to experience
	problems running Flight Simulator, make sure you have enough expanded memory
	available. Please refer to the Flight Simulator user's guide for more
	information.
	
	Additional query words: 5.00 5.00a 5.10 fltsim cannot memory fs51 flightsim can't can not
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsetup kbimu 
	Technology        : kbGamesSearch kbFlightSimSearch kbFlightSim500DOS kbFlightSim510DOS kbSimSearch
	Version           : :5.0,5.1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
