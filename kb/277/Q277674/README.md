---
layout: page
title: "Q277674: SMS: Smsiddup Identifies Current and Historical Duplicates"
permalink: /kb/277/Q277674/
---

## Q277674: SMS: Smsiddup Identifies Current and Historical Duplicates

{% raw %}

	Article: Q277674
	Product(s): Microsoft Systems Management Server
	Version(s): 1.2
	Operating System(s): 
	Keyword(s): kbsms120 kbsms120bug
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Smsiddup.exe utility is included with Systems Management Server (SMS) 1.2
	Service Pack 4 (SP4) to identify duplicate SMSIDs that may be produced as a
	result of "cloning" SMS clients. Even if duplicates that are identified by
	Smsiddup have been removed and their inventory records have been removed from
	the SMS Administrator console, Smsiddup may still report their presence in
	subsequent reports.
	
	CAUSE
	=====
	
	Smsiddup produces a report of duplicate SMSIDs that are contained not only in
	current hardware inventory but also in hardware inventory history. Therefore, if
	computers that are identified as having duplicate SMSIDs are deleted in the SMS
	Administrator console, they are still identified by Smsiddup because the current
	inventory record is moved to inventory history instead of being deleted. This
	SMS functionality is by design.
	
	Because inventory history is typically purged by using the Delete Special command
	in the SMS Administrator console, duplicate SMSIDs are eventually removed from
	the database completely. (See the "More Information" section of this article for
	information about using the Delete Special command.)
	
	If you depend on the Smsiddup reports to identify current duplicates, it can
	become difficult to distinguish current duplicates from those that have already
	been deleted. The hotfix that is described in this article enables you to
	optionally delete inventory records that are identified as duplicates by
	Smsiddup.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date     Time   Version  Size   File name     Platform
	  ------------------------------------------------------
	  9/22/00  18:13  786      15 KB  Smsiddup.exe  Intel
	  9/22/00  18:13  786      22 KB  Smsiddup.exe  Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.`
	
	MORE INFORMATION
	================
	
	The updated version of Smsiddup.exe includes an option to delete duplicate
	SMSIDs from inventory history. Smsiddup does not delete duplicate SMSIDs that
	are current and visible in the SMS Administrator console. You must therefore
	delete the duplicate SMSIDs when duplicate SMSIDs are first reported.
	When you use the option to delete duplicate SMSIDs, those computer records that
	are identified are deleted from inventory history. This does not affect the
	inventory history for other computers for which that inventory history may be
	required for reporting purposes. This prevents you from having to use the Delete
	Special command with the "Machine history records older than 0 days" setting to
	purge all duplicate SMSIDs from the database.
	
	Interactive and Command-Line Use of the Updated Smsiddup.exe
	------------------------------------------------------------
	
	When you use the updated Smsiddup tool with no command-line arguments, Smsiddup
	prompts you for the following information:
	
	  Enter SQL Server name:
	  Enter database name:
	  User:
	  Enter password:
	  Delete historical duplicate ?(Y/N):
	
	The following command-line arguments and order are supported with the updated
	tool:
	
	  smsiddup <sqlservername> <sqllogonid> <password>
	  <databasename> <Y/N to delete duplicates>
	
	For example: smsiddup smssqlsrv sa sapasswd sms y
	
	Note that the last parameter can be ignored and defaults to N (No).
	
	Smsiddup also supports Microsoft SQL Server integrated security. If you are using
	integrated security with the interactive use of Smsiddup, you can leave the
	logon and password entries blank. In command-line mode, use quotation marks (")
	to delimit the logon and password entries. For example:
	
	  smsiddup smssqlsrv "" "" sms y
	
	Using the "Delete Special" Command to Delete Computer History
	-------------------------------------------------------------
	
	The deletion of inventory history in SMS 1.2 is not an automatic process.
	Computer history grows as computers supply inventory data that contains
	differences in the information that is supplied in subsequent inventory MIF
	files. For example, disk information such as "%Disk Full" for hard disks changes
	regularly as files are saved and deleted from the disk. You should delete
	inventory history as an administrative task at regular intervals to delete
	inventory history that is older than a predetermined age.
	
	The Delete Special command is available on the Edit menu in the SMS Administrator
	console while the Sites window is active (or has the focus). The default option
	is to delete computers with the last activity. To delete computer history
	records, click Machine History Records in the Delete box. You can purge computer
	history records from the SMS database based on dates or age.
	
	Deleting history records is a two-step process. In the first step, you use the
	Delete Special command as described above. This purges the computer records but
	does not actually delete the inventory information that is recorded in other SMS
	SQL database tables. This data effectively becomes "orphaned" and must be
	deleted in the second step. In the second step, you use the SMS Database Manager
	tool (Dbclean). On the Tools menu, click Delete Unused Common/Specific Records.
	This command deletes the orphaned inventory data that was created in the first
	step.
	
	Additional query words: prodsms smsiddup exe
	
	======================================================================
	Keywords          : kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS120
	Version           : :1.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
