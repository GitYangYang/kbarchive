---
layout: page
title: "Q265733: XADM: How to Disable Public Folder Conflict Message Notification"
permalink: /kb/265/Q265733/
---

## Q265733: XADM: How to Disable Public Folder Conflict Message Notification

{% raw %}

	Article: Q265733
	Product(s): Microsoft Exchange
	Version(s): winnt:5.0,5.5
	Operating System(s): 
	Keyword(s): exc5 exc55
	Last Modified: 23-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article explains how to disable public folder conflict message
	notification.
	
	MORE INFORMATION
	================
	
	When two users have edited and modified the same message in a public folder, the
	resulting saved messages are defined as being in conflict. This can happen when
	a simultaneous save occurs on the same public folder server, or if the message
	is edited on two servers that contain replicas of the folder. In this case, the
	conflict occurs when replication between the servers takes place.
	
	When a conflict occurs, the owners of the public folder receive an e-mail message
	from the Exchange server notifying them of the conflict. The owners can then
	open the conflicting message in the public folder where they can choose to keep
	the item or keep all items. Keeping all items results in the generation of two
	messages in the public folder.
	
	The method Exchange uses to resolve these conflicts is defined by the folder
	property, PR_RESOLVE_METHOD. This property is displayed as an unassigned folder
	property under the process identifier, 0x3FE7. There are three possible values
	for this property:
	
	  0	RESOLVE_METHOD_DEFAULT
		Default handling of message conflicts
	  1	RESOLVE_METHOD_LAST_WRITER_WINS
		Last writer will win the conflict.
	  2	RESOLVE_METHOD_NO_CONFLICT_NOTIFICATION
		Same steps as the RESOLVE_METHOD_DEFAULT, except that the
		contacts defined on a folder and the modifiers of a message
		are not notified.
	
	By default, the value is set to 0. If you do not want a notification message to
	be sent out during a conflict, then you must change the value to 2.
	
	You can only change this value programmatically. For more information, you can
	consult the Microsoft Developer Network (MSDN), or you can use a utility such as
	Mdbvu32.exe to change individual folder property values.
	
	The MSDN information is available on the Microsoft Web site at
	http://www.microsoft.com/msdn; search for PR_RESOLVE_METHOD for more
	information.
	
	The utility, Mdbvu32.exe, is included with the Exchange Server CD-ROM under the
	Support/Utilities directory. For additional information about how to use
	Mdbvu32.exe, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q214816 HOWTO: Use Mdbvu32.exe to Set/Create a Property on a Folder
	
	Using Mdbvu32.exe to Change the Value of PR_RESOLVE_METHOD
	----------------------------------------------------------
	
	Note: The MAPI profile used with Mdbvu32.exe must have the necessary rights to
	modify public folder attributes. A profile with the service account defined as
	the Microsoft Windows NT Associated account is recommended.
	
	1. Open Mdbvu32.exe, and then click OK to log on to the information store.
	
	2. In the MDB menu, click OpenMessageStore.
	
	3. Select Public Folders, and then click Open.
	
	4. In the MDB menu, click Open Root Folder. Click OK until the main window
	  appears.
	
	5. Double-click IPM_SUBTREE.
	
	6. Choose the public folder that you wish to not receive notification messages,
	  and then double-click this folder.
	
	7. In the Folder Properties window, double-click the property 0x3FE7.
	
	8. In the Current Properties window select 0x3FE7, and then click SetProps.
	
	9. In the Property ID window, type in "3FE7" (without the quotation marks).
	
	10. For PropType, select PT_LONG.
	
	11. Add the value for this property under Prop Data; in this case enter "2"
	  (without the quotation marks).
	
	12. Click Add, and then click Call.
	
	13. Click close on the next window, and make sure the value for 0x3FE7 updated
	  to reflect the changes you made.
	
	14. Close the window and repeat these steps for other folders.
	
	Important: By modifying the parent folder property value, the value is not
	propagated to child folders. Also, when a child folder is created under the
	parent folder with a modified value, the child folder does not inherit the
	modified value and is created with the default value of 0.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc5 exc55 
	Component         : Admin
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : winnt:5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
