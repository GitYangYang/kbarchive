---
layout: page
title: "Q118927: PC Adm: Setting Passwords Using the Administrator Program"
permalink: /kb/118/Q118927/
---

## Q118927: PC Adm: Setting Passwords Using the Administrator Program

{% raw %}

	Article: Q118927
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.0,3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, versions 3.0, 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	An administrator of a Microsoft Mail for PC Networks postoffice can use the Mail
	Administrator program (ADMIN.EXE) to set two different kinds of passwords. Each
	postoffice will have one password to control dial-in access to the postoffice,
	and each mailbox will have a password to provide security for the users' mail.
	This article provides information about the two kinds of passwords and how you
	can change them.
	
	MORE INFORMATION
	================
	
	The sections below list the ADMIN.EXE program commands you can use to manage
	these passwords. For information about how to start the Mail Administrator
	program, please see the Microsoft Mail for PC Networks "Administrator's Guide."
	
	Postoffice Password Commands
	----------------------------
	
	The following command
	
	  Config, Password, Sign-on password to this postoffice:
	
	sets the postoffice password to provide security for dial-in access via modem
	(for example, Microsoft Mail Remote for Windows users, or when you use the
	External Mail program with a postoffice connected via modem.)
	
	For additional information about setting passwords using the Mail Remote client,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q97894 PC WRmt: Remote Mail Password Dialogs
	
	When you add an external postoffice and configure it as a direct route type via
	modem, use the following command to specify the password for the external
	postoffice it will dial to:
	
	  " External-Admin, Setup, Enter network name:, Password " (without the
	  quotation marks)
	
	You do not need a password for indirect route postoffices or direct route
	postoffices via an MS-DOS drive.
	
	Mailbox Password Commands
	-------------------------
	
	The following command
	
	  Local-Admin, Options, Password, Password:
	
	is the default password for new users. If you would like the default password for
	the postoffice to be something other than "password," you can change it here.
	
	When you create a new mailbox, the "Password:" field contains the default
	password. You can change the password with the following command
	
	  Local-Admin, Create, Mailbox name:, Password:
	
	or let the user change it using Microsoft Mail for Windows.
	
	If a user forgets his or her password, you can reset it to the default using the
	command:
	
	  Local-Admin, Recover, <mailbox name>, Yes
	
	To change the password for a mailbox that already exists, you must use
	appropriate client software:
	
	  Client                  Command
	  ---------------------------------------------
	  MS-DOS                  Options, Password
	  Windows                 Mail, Change Password
	  Macintosh               File, Change Password
	  Presentation Manager    Mail, Change Password
	
	In each product, you will be asked to enter the old password, then enter the new
	password twice for verification.
	
	REFERENCES
	==========
	
	For more information about this topic, please see the Microsoft Mail
	"Administrator's Guide":
	
	Version 3.0
	  Default passwords, page 95.
	  External Admin Setup command, page 113.
	  Lost passwords, page 99.
	  Postoffice password, page 134.
	
	Version 3.2
	  Default passwords, page 101.
	  External Admin Setup command, page 119.
	  Lost passwords, page 104.
	  Postoffice password, page 74.
	
	Additional query words: 3.00 3.20 admin
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN320 kbMailPCN300
	Version           : WINDOWS:3.0,3.2
	
	=============================================================================
	

{% endraw %}
