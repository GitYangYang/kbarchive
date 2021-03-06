---
layout: page
title: "Q258536: FIX: UPARROW Key Doesn't Work in Code Editor in Hebrew Windows"
permalink: /kb/258/Q258536/
---

## Q258536: FIX: UPARROW Key Doesn't Work in Code Editor in Hebrew Windows

{% raw %}

	Article: Q258536
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbMiscTools kbvfp600 kbvfp600bug kbGrpDSFox kbDSupport kbVS600sp4fix kbVS600sp4 kbVS600
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run Visual FoxPro under Hebrew-Enabled Microsoft Windows and you use
	the UP ARROW key to move around in a code editor, the UP ARROW key does not work
	as expected.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article. This bug was corrected in the latest
	service pack for Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the following
	article numbers to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	To download the latest Visual Studio service pack, visit the following Microsoft
	Web site:
	
	  http://msdn.microsoft.com/vstudio/downloads/updates.asp
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Run Visual FoxPro 6.0 under Hebrew-Enabled Windows 98.
	
	2. In Visual FoxPro, create a program (.prg).
	
	3. Before typing anything in the .prg, follow these steps in the code editor:
	
	  a. Press the TAB key and then type "This is a Test" (without the quotation
	     marks).
	
	  b. Press the ENTER key to move the cursor to the second line.
	
	  c. On the second line, press the BACKSPACE key to move the cursor to the
	     beginning, and then type "This is a second line" (without the quotation
	     marks).
	
	  d. Then, press the HOME key to move the cursor back to the beginning of the
	     second line.
	
	  e. Press the UP ARROW key.
	
	NOTE: At this point, when the UP ARROW key is pressed, the cursor stays in the
	same location and does not move up to the line above it.
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbMiscTools kbvfp600 kbvfp600bug kbGrpDSFox kbDSupport kbVS600sp4fix kbVS600sp4 kbVS600sp5fix 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
