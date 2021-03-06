---
layout: page
title: "Q89912: File Drag May Not Work with Quick Recorder"
permalink: /kb/089/Q89912/
---

## Q89912: File Drag May Not Work with Quick Recorder

{% raw %}

	Article: Q89912
	Product(s): Miscellaneous Windows Products
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Sound System, versions 1.0, 1.0a, 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Windows Sound System Quick Recorder is not aware of an application's
	object-linking-and-embedding (OLE) capability nor of the information an
	application needs to conduct an OLE operation, such as receiving a file from
	Quick Recorder.
	
	NOTE: The OLE functionality of Quick Recorder is OLE version 1.0 with the
	exception of the drag and drop capability which is OLE version 2.0.
	
	MORE INFORMATION
	================
	
	By default, Quick Recorder looks for an Edit menu with a Paste or Paste Link
	command when you attempt to drag a sound file to another application. Some
	applications do not have the same default menu or commands. To allow Quick
	Recorder to successfully drag a file, you must change the menu and commands for
	which Quick Recorder looks.
	
	To change the target menu and commands in Quick Recorder:
	
	1. Open the target application and check the menu command you want to execute
	  when performing a drag operation.
	
	2. Start Quick Recorder.
	
	3. From the Options menu, choose Preferences.
	
	4. Select Embedded Object.
	
	5. Press CTRL+SHIFT while dragging the file to the target application.
	
	6. A dialog box appears with two edit fields: Main Menu Item Name and Sub Menu
	  Item Name.
	
	7. Type the name of the menu in the Main Menu Item Name field, and the name of
	  the command in the Sub Menu Item Name field (these name fields are case
	  sensitive).
	
	8. Choose the OK button to save the changes.
	
	9. Repeat steps 2 through 8, and select Link To Object in step 4.
	
	You must repeat these steps for each application whose OLE menu and commands do
	not match the Quick Recorder defaults.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinSoundSysSearch kbWinSoundSys100 kbWinSoundSys100a kbWinSoundSys200
	
	=============================================================================
	

{% endraw %}
