---
layout: page
title: "Q175768: FIX: ActiveX MAPI Control 5.0 Causes Memory Errors"
permalink: /kb/175/Q175768/
---

## Q175768: FIX: ActiveX MAPI Control 5.0 Causes Memory Errors

{% raw %}

	Article: Q175768
	Product(s): Microsoft FoxPro
	Version(s): WINNT:97
	Operating System(s): 
	Keyword(s): kbvfp kbvfp600fix
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you add a MAPISession control version 5.0 or a MAPIMessages control version
	5.0 to a form and then edit the (Messaging Application Programming Interface)
	MAPI control properties, a memory corruption error appears.
	
	RESOLUTION
	==========
	
	One possible resolution is to copy the older Msmapi32.ocx version 1.0.2815 from
	another computer that is currently running Visual FoxPro version 5.0 or extract
	the file from the Visual FoxPro 5.0 install disks.
	
	For additional information on using the extract utility, please see the following
	article in the Microsoft Knowledge Base:
	
	  Q135518 HOWTO: Copy Files from Cabinets on DMF-Formatted Disks
	
	NOTE: This resolution will only work as long as another application does not
	install version 5.0 of the Msmapi32.ocx over version 1.0.2815. These
	applications may include Visual Basic version 5.0, Visual FoxPro for Windows
	version 5.0a or an executable file created by one of these applications.
	
	NOTE: This error has not been corrected in Service Pack 1 or Service Pack 2.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This has been corrected in Visual FoxPro 6.0.
	
	MORE INFORMATION
	================
	
	Once you try to edit or make changes to any of the MAPISession control or
	MAPIMessages control specific properties, the following error is displayed:
	
	  OLE Idispatch exception code 0 from MAPISession: Property is write-only.
	
	  -or-
	
	  OLE Idispatch exception code 0 from MAPIMessages: Property is write-only.
	
	This will not prevent the control from being edited. Click OK and then
	right-click the control to display the short-cut menu. Choose MAPISession or
	MAPIMessage Properties to open the Property Pages dialog box. Change one of the
	properties then click Apply or OK. In Windows 95, the following error message
	appears:
	
	  This program performed an illegal operation and will be shut down.
	
	After clicking the Details push button, the following message appears:
	
	  VFP caused and invalid pagefault in module KERNEL32.DLL at <register
	  address>.
	
	In Windows NT 4.0, the following error appears:
	
	  An application error had occurred and an application error log is being
	  generated. VFP.EXE Exception: access violation.
	
	NOTE: If you get this error multiple times, the error log file may get larger.
	You may delete the User.dmp file to free up the space used by this log file.
	
	Steps to Reproduce Behavior
	---------------------------
	
	The following two methods reproduce the application error. Method 1:
	
	1. Create a new form.
	
	2. In the Tools Options menu, click the Controls tab. Click ActiveX controls,
	  then scroll down the list and select both Microsoft MAPI Messages Control,
	  version 5 and Microsoft MAPI Session Control, version 5. Click OK.
	
	3. On the Form Controls toolbar, click the View Classes button and select
	  ActiveX Controls.
	
	4. Click one of the MAPI controls and add it to the form.
	
	5. Save and run the form.
	
	6. Modify the form. Right-click on the control. The write-only message described
	  appears. Click OK. Right-click the control again and select Microsoft MAPI
	  Message (or Session) Control Properties.
	
	7. Change any of the properties and choose OK or Apply.
	
	Method 2:
	
	1. Follow steps 1-3 in Method 1 above.
	
	2. Before you add one of the MAPI ActiveX controls to the form, close the
	  Properties sheet of the form if it is open.
	
	3. Click one of the MAPI controls and add it to the form.
	
	4. Right-click on the control and select Microsoft MAPI Message (or Session)
	  Control Properties.
	
	5. Make a change to any of the properties and click OK.
	
	6. Click on the form to re-gain focus. Right-click on the form and choose
	
	Properties to open the Properties sheet.
	
	1. Right-click on the MAPI control again. The write-only message described above
	  appears. Click OK. Right-click the control again and select Properties.
	
	2. Change any of the properties and click OK or Apply.
	
	(c) Microsoft Corporation 1997, All Rights Reserved. Contributions by Dean
	Christopher, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp kbvfp600fix 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : WINNT:97
	Issue type        : kbbug kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
