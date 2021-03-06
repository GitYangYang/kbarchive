---
layout: page
title: "Q140153: Music Central and Cinemania Fonts on CD Are Not Reinstalled"
permalink: /kb/140/Q140153/
---

## Q140153: Music Central and Cinemania Fonts on CD Are Not Reinstalled

{% raw %}

	Article: Q140153
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1996 edition; WINDOWS:95
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Cinemania for Windows 1996 edition 
	- Microsoft Music Central for Windows 1996 edition 
	- the operating system: Microsoft Windows 95 
	- the operating system: Microsoft Windows 98 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you delete the following fonts from your computer and then install Cinemania
	or Music Central, the fonts in the Data\Setup folder on the CD-ROM are not
	installed in your Windows Fonts folder.
	
	The fonts are:
	
	- Arial.ttf     Arial (TrueType)
	- Msref1.ttf    MS Reference 1 (TrueType)
	- Msref2.ttf    MS Reference 2 (TrueType)
	- Times.ttf     Times New Roman (TrueType) - Music Central only
	
	Removing Music Central or Cinemania, and then reinstalling normally reinstalls
	these fonts. However, the fonts are not reinstalled if the font files have been
	deleted from the hard disk.
	
	CAUSE
	=====
	
	The fonts included on the Music Central and Cinemania compact disc are not
	installed on the computer if Windows reports that these fonts are already
	installed. This can happen if the font files have been deleted directly from the
	hard disk rather than being removed through the Fonts tool in Control Panel.
	
	RESOLUTION
	==========
	
	To manually install or re-install a font from the compact disc, follow these
	steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Fonts.
	
	3. On the File menu, click Install New Font.
	
	4. The Add Fonts dialog box appears. In the drives area, select the CD-ROM
	  drive, which is usually drive D.
	
	5. Double-click the Data folder, and then double-click the Setup folder.
	
	6. Click the font you want to add. To select more than one font at a time, hold
	  down the CTRL key while you click each font.
	
	7. Make sure the Copy Fonts To Fonts Folder check box is selected.
	
	8. Click OK.
	
	Additional query words: '96 96 multi media multimedia multi-media mmtitles kbmm font text missing gone
	
	======================================================================
	Keywords          :  
	Technology        : kbOSWin98 kbOSWin95 kbOSWinSearch kbHomeProdSearch kbHomeMMsearch kbCineManiaSearch kbCinemania1996 kbMusicCentral kbMusicCentral1996
	Version           : :1996 edition; WINDOWS:95
	
	=============================================================================
	

{% endraw %}
