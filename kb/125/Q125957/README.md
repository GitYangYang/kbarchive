---
layout: page
title: "Q125957: Explorapedia: Cannot Hear Tad's Narration"
permalink: /kb/125/Q125957/
---

## Q125957: Explorapedia: Cannot Hear Tad's Narration

{% raw %}

	Article: Q125957
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): kbfaq
	Last Modified: 29-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Explorapedia series: World of Nature for Windows, version 1.0 
	- Microsoft Explorapedia series: World of People for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Explorapedia, you may not be able to hear Tad's narration, although you can
	hear other sounds, such as those associated with transitions and hot spots.
	
	CAUSE
	=====
	
	8-Bit Compressed Sounds
	-----------------------
	
	This problem occurs because most of the sounds in Explorapedia are 8-bit
	uncompressed sounds. Tad's voice, however, consists of 8-bit compressed sound.
	Compressed sound requires specific sound driver software to decompress it prior
	to playback. See the "8-Bit Compressed Sounds Solution" section below for a
	resolution.
	
	"S" Missing on Win.ini MCI Extensions
	-------------------------------------
	
	Sometimes Tad's voice is not heard because there is no "s" on MCI Extension(s) in
	the Win.ini file. AutoDesk Animations, a third-party program, deletes the "s" on
	MCI Extension(s) in Win.ini, so Explorapedia does not recognize the MCI section
	in the Win.ini file. See the "Missing 'S' Solution" section below for a
	resolution.
	
	RESOLUTION
	==========
	
	Missing "S" Solution
	--------------------
	
	If the "s" is missing on the MCI Extensions section of Win.ini, replace it using
	a text editor such as Notepad to edit your Win.ini file. For more information
	about editing your Win.ini file, see you Windows online Help.
	
	8-Bit Compressed Sounds Solution
	--------------------------------
	
	Check to see if Tad's voice has been turned off. Tad's voice can be turned on and
	off by clicking on Settings in the Spaceship, then click Sounds, then click
	Tad's Voice.
	
	If Tad's voice is set to On in Settings, and you still can't hear his voice, use
	the following steps to resolve the problem:
	
	1. Verify that the [MCI] Sound driver is installed in the Drivers Control Panel.
	  If it is not there, install it.
	
	  For more information about how to perform this task in Windows, see your
	  Windows printed documentation or online Help.
	
	2. If Step 1 does not resolve the problem, please see the following article in
	  the Microsoft Knowledge Base:
	
	  Q121132 MSACM 2.0: Compressed Audio Will Not Play
	
	3. If Step 1 or 2 does not resolve the problem, please see the following article
	  in the Microsoft Knowledge Base:
	
	  Q106549 Compressed Audio Doesn't Play on Sound Blaster Card
	
	After following the above instructions, you should be able to run Explorapedia
	and hear Tad's narration.
	
	
	Additional query words: 1.00 mskids kids homekids explora tad spaceship animation narrate tadpole sound people nature world of
	
	======================================================================
	Keywords          :  kbfaq
	Technology        : kbHomeMMsearch kbZNotKeyword2 kbExplorapediaNature100 kbExplorapediaPeople100
	Version           : WINDOWS:1.0
	
	=============================================================================
	

{% endraw %}
