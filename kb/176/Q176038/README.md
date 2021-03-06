---
layout: page
title: "Q176038: XCLN: Attachments Show {EMBED Unknown} Instead of Icon"
permalink: /kb/176/Q176038/
---

## Q176038: XCLN: Attachments Show {EMBED Unknown} Instead of Icon

{% raw %}

	Article: Q176038
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0; :8.0,8.01,8.02,8.03
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 3.x client, versions 4.0, 5.0 
	- Microsoft Exchange Windows 95/98 client, versions 4.0, 5.0 
	- Microsoft Exchange Windows NT client, versions 4.0, 5.0 
	- Microsoft Outlook 97, versions 8.0, 8.01, 8.02, 8.03 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you receive an e-mail message with an attachment, one of the following may
	appear in place of the icon associated with the application for the attachment:
	
	{EMBED Outlook.FileAttach}
	
	-or-
	
	{EMBED WordMailFileAttachment}
	
	-or-
	
	{EMBED Unknown}
	
	CAUSE
	=====
	
	The Show Field Codes option is enabled.
	
	WORKAROUND
	==========
	
	To resolve this problem, perform any one of the following:
	
	Disable Word as your E-mail Editor.
	
	-or-
	
	Press the ALT+F9 keystroke to disable Show Field Codes.
	
	-or-
	
	With the e-mail message open, select Options from the Tool menu, and then
	deselect Show Field Codes
	
	MORE INFORMATION
	================
	
	Fields are used as placeholders for data that might change in a document and for
	creating form letters and labels in mail-merge documents. Some of the most
	common fields are the PAGE field, which is inserted when you add page numbers,
	and the DATE field, which is inserted when you click Date and Time on the Insert
	menu and then select the Update Automatically check box. Fields are inserted
	automatically when you create an index or table of contents by using the Index
	and Tables command on the Insert menu. You can also use fields to automatically
	insert document information (such as the author or file name), to perform
	calculations, to create links and references to other documents or items, and to
	perform other special tasks.
	
	Field codes appear between curly brackets or braces [ { } ]. To display the
	results of the field codes such as the results of calculations, hide the field
	codes by doing the following:
	
	1. Click Options on the Tools menu, and then click the View tab.
	
	2. Clear the Field Codes check box.
	
	Fields are somewhat like formulas in Microsoft Excel. The field code is like the
	formula, and the field result is like the value that the formula produces.
	
	You cannot insert field braces by typing characters on the keyboard. Fields are
	inserted when you use particular commands, such as the Date and Time command on
	the Insert menu, or when you press CTRL+F9 and type the appropriate information
	between the field braces.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbExchangeSearch kbExchange500 kbExchange400 kbExchangeClientSearch kbZNotKeyword kbOutlook97 kbZNotKeyword2 kbOutlook97Search kbZNotKeyword3 kbOutlook801 kbOutlook802 kbOutlook803 kbExchange400NT kbExchange500NT kbExchange400Win95 kbExchange500Win95
	Version           : WINDOWS:4.0,5.0; :8.0,8.01,8.02,8.03
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
