---
layout: page
title: "Q168256: HOWTO: Programmatically Launch Dial-Up Networking Connection"
permalink: /kb/168/Q168256/
---

## Q168256: HOWTO: Programmatically Launch Dial-Up Networking Connection

{% raw %}

	Article: Q168256
	Product(s): Microsoft FoxPro
	Version(s): 3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbsetup kbvfp300 kbvfp500 kbvfp600
	Last Modified: 28-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Using the FoxPro RUN command, it is possible to programmatically launch a
	Windows 95 Dial-Up Networking connection.
	
	MORE INFORMATION
	================
	
	
	The following syntax can be used to launch a Dial-Up Networking (DUN)
	connection:
	
	     RUN /N Rundll Rnaui.dll,RnaDial <your DUN connection name>
	
	For a connection named Test, use the following command to launch this
	connection:
	
	     RUN /N Rundll Rnaui.dll,RnaDial Test
	
	The function call RnaDial and the connection name are both case-sensitive.
	
	NOTE: Although there is a function within the Rnaui.dll file that enables you to
	programmatically dial, a function that allows you to programmatically disconnect
	is not available.
	
	To view the functions available within Rnaui.dll or any .dll file, find the file,
	use the right mouse button (right-click) to select the file, and select
	QuickView. You can view the available programmatic functions from the listing
	under Export Table.
	
	If QuickView is not available as a selection then QuickView needs to be
	installed. You can install QuickView using the Control Panel by selecting
	Add/Remove Programs, and then selecting the Windows 95 (or Windows NT) Setup
	tab. Next, click Accessories and select QuickView.
	
	Below is the Export Table of available functions from the Rnaui.dll file:
	
	  Export Table
	  ------------
	  Name:  Rnaui.dll
	  Characteristics:  00000000
	  Time Date Stamp:  320c06ce
	  Version:  0.00
	  Base:  00000001
	  Number of Functions:  00000009
	  Number of Names:  00000009
	
	  Ordinal     Entry Point        Name
	  -----------------------------------------
	  0000         0000773e     DllCanUnloadNow
	  0001         00002a80     DllGetClassObject
	  0002         00007880     Remote_CreateEntry
	  0003         000029ef     Remote_CreateInstance
	  0004         00003988     Remote_EditEntry
	  0005         00003260     Remote_Notify
	  0006         000031b9     RnaDial
	  0007         000031da     RnaRunImport
	  0008         00007a6a     RnaWizard
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	Q135338 HOWTO: View Exported Functions in a DLL
	
	Additional query words: kbdse
	
	======================================================================
	Keywords          : kbsetup kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : :3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
