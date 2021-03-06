---
layout: page
title: "Q267851: Automap Err Msg: Cannot Display End User License Agreement"
permalink: /kb/267/Q267851/
---

## Q267851: Automap Err Msg: Cannot Display End User License Agreement

{% raw %}

	Article: Q267851
	Product(s): Microsoft Automap
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kberrmsg kbfile kbimu
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MapPoint 2002 
	- Microsoft MapPoint 2001 
	- Microsoft Streets & Trips 2002, version 1.0 
	- Microsoft Streets and Trips 2001 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start Microsoft MapPoint 2001 or Microsoft Streets and Trips
	2001 or Streets & Trips 2002 for the first time, you may receive the
	following error message:
	
	  EULA Error
	
	  This application cannot display the End User License Agreement. This agreement
	  must be displayed and accepted prior to running this application for the
	  first time. Please reinstall the application you are trying to run.
	
	RESOLUTION
	==========
	
	To resolve this issue, read the End User License Agreement for MapPoint 2001 or
	Streets and Trips 2001 or Streets & Trips 2002, and then download and run
	the Steula.exe file:
	
	1. Quit all programs that are running on your computer.
	
	2. Click Start, and then click Run.
	
	3. In the Open box, type the appropriate line (including the quotation marks)
	  for the program that you attempted to start, and then click OK.
	
	  MapPoint 2001
	  -------------
	
	  "<drive>:\program files\common files\microsoft shared\works
	  shared\mpn8eula.txt"
	
	  MapPoint 2002
	  -------------
	
	  "<drive>>:\program files\common files\microsoft shared\works
	  shared\mpn9eula.txt"
	
	  Streets and Trips 2001
	  ----------------------
	
	  "<drive>:\program files\common files\microsoft shared\works
	  shared\stn8eula.txt"
	
	  Streets and Trips 2002
	  ----------------------
	
	  "<drive>:\program files\common files\microsoft shared\works
	  shared\stn9eula.txt"
	
	  where <drive> is the drive letter of the hard disk on which Microsoft
	  Windows is installed.
	
	4. Read the End User License Agreement (EULA) for the program that you want to
	  install. If you agree to the terms in the EULA, proceed to the next step
	
	5. On the File menu, click Exit.
	
	6. Download and run the Steula.exe file.
	
	  NOTE: This file modifies the Microsoft Windows registry to indicate that you
	  have accepted the End User License Agreement for the program.
	
	The following file is available for download from the Microsoft Download Center:
	
	  Steula.exe
	  (http://download.microsoft.com/download/streetstrips2000/Update/1.0/W98NT42KMe/EN-US/Steula.exe)
	
	Release Date: Jul-14-2000
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q317904 Money/ Street/ Works 2002: 'EULA Error' Error Message When You Start
	  Program
	
	Additional query words: mp2001 map point st2001 eula
	
	======================================================================
	Keywords          : kberrmsg kbfile kbimu 
	Technology        : kbHomeProdSearch _IKkbbogus kbExpediaSearch kbMapptSearch kbMapPoint2001 kbExpediaStreets2001 kbExpediaStreets2002 kbMapPoint2002
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
