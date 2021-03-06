---
layout: page
title: "Q254735: SMS: How to Clean Up Duplicate Computer IDs"
permalink: /kb/254/Q254735/
---

## Q254735: SMS: How to Clean Up Duplicate Computer IDs

{% raw %}

	Article: Q254735
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbClient kbConfig kbDatabase kbsms200 kbCollections kbInventory kbQuery kbsmsAdmin
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to find and clean up Microsoft Systems Management
	Server 2.0 clients that use the same unique identifier. The Systems Management
	Server Unique ID property is used to distinguish Systems Management Server
	clients. It is important that this value stay unique for each client.
	
	You may have duplicate IDs in your environment if you "clone" workstations that
	have the Systems Management Server client installed or if you have remnants from
	a previous Systems Management Server client installation (such as the Sms.ini or
	Smscfg.ini file).
	
	Duplicate IDs can cause behaviors such as high central processing unit (CPU)
	usage, incorrect inventory reporting, advertisements run by the wrong clients,
	and other unexpected events. To help avoid these behaviors, it is important to
	clean up duplicate IDs as soon as possible if you encounter them.
	
	MORE INFORMATION
	================
	
	To determine if you have duplicate IDs, create a Systems Management Server query
	based on the following sample query:
	
	  select * from sms_g_system_SYSTEM as g INNER JOIN sms_gh_system_SYSTEM as h
	  on g.ResourceId = h.ResourceId where g.Name <> h.Name
	
	When you run this query, you see all of the different computer names that are
	using the same ID. Note that multiple-boot clients or clients that have been
	renamed also appear as duplicates. After you find the duplicates, allocate a new
	ID to these workstations. There are two methods for allocating a new ID to a
	client.
	
	Manual Method
	-------------
	
	To manually clean up a client, run the 20clicln.bat file to uninstall the Systems
	Management Server client. When this process is finished, delete any instance of
	the Sms.ini or Smscfg.ini file on the workstation. After this is complete,
	reinstall the client by using normal installation methods. A new ID will be
	allocated to the client. BR/>
	The version of 20CliCln.bat that can be downloaded as part of the SP2 support
	tools can be run with a command line switch of /scrub which removes the
	Smscfg.ini file and enable a creation of a new GUID. It does not remove the
	Sms.ini left over from a SMS 1.2 client.
	
	Software Distribution Method
	----------------------------
	
	If you have numerous computers that need a new Systems Management Server ID, you
	can use the Microsoft BackOffice Resource Kit 4.5 Newuid.exe utility. Create a
	package by using the utility with the "Newuid.exe /s" command, which causes the
	utility to run silently. You need to create a collection that contains all of
	the workstations that have a duplicate ID. Use a query based on the following
	sample query:
	
	  select distinct r.Name, r.OperatingSystemNameandVersion,
	  r.ResourceDomainORWorkgroup, r.LastLogonUserDomain, r.LastLogonUserName,
	  r.SMSUniqueIdentifier, r.ResourceId from SMS_R_System as r,
	  SMS_GH_System_SYSTEM as h, SMS_G_System_SYSTEM as g where g.ResourceID =
	  h.ResourceID and g.Name <> h.Name and r.ResourceID = g.ResourceID
	
	Make sure to remove any carriage returns from this query before pasting it into
	the Edit Query window for this collection. If you do not remove the carriage
	returns, the query is not saved because of improper syntax.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q234262 SMS: Linking Query to a Collection Membership Rule May Not Work
	
	After you create this collection, you may not see the same number of clients as
	you did in the first query. This occurs because this query returns only a unique
	list of duplicate IDs. After you advertise the Newuid.exe package to this
	collection, all the clients listed in the previous query run the program because
	these workstations are all sharing the same IDs (the same globally unique
	identifiers, or GUIDs).
	
	When you run Newuid.exe, use the "Newuid.exe /s /allocate" command enables the
	clients to get a new ID and retain client functionality. The /s switch causes
	the installation to run silently.
	
	NOTE:When the /allocate switch is used, Newuid.exe attempts to run Smsboot1.exe
	from a logon point. Access to a logon point requires that a user be logged on.
	If no user is logged on, the GUID that exists is deleted, but a new GUID is not
	allocated until Smsls.bat or Smsman.exe is executed.
	
	NOTE: You do not receive confirmation that the clients have successfully run the
	program if you do not use the /allocate switch. After Newuid.exe has been run
	without the /allocate switch, all client communication with the client access
	point (CAP) stops until the client either runs Smsls.bat or Smsman.exe or has
	been reinstalled by using the Microsoft Windows NT Remote Client installation.
	Client functionality does not return and the new ID is not allocated until the
	client has used one of these installation methods.
	
	After you have cleaned up the duplicate IDs, purge the inventory history in your
	database. Use the Delete Aged Inventory History task under Tasks under Database
	Maintenance in the Systems Management Server console to delete all history older
	than one day. You can set this value back to its previous value after you have
	all of your client inventory back and have you have verified that there are no
	more duplicates in your environment.
	
	By changing the settings for the Database Maintenance Tasks, all data in your
	database older than one day may be removed. This is fine in many situations,
	however, if you only have a small percentage of your inventory which is
	duplicated, this may not be appropriate.
	
	In such a case, use the white paper, Managing Duplicate Microsoft Systems
	Management Server Unique Identifiers, which may provide a better solution, which
	is located at the following Microsoft Web site:
	
	  http://www.microsoft.com/smsmgmt/techdetails/newuid.asp
	
	NOTE: This paper discusses the process of only removing the history information
	for the duplicate computers, not the entire database.
	
	Additional query words: prodsms 20clicln.bat sms.ini newuid.exe
	
	======================================================================
	Keywords          : kbClient kbConfig kbDatabase kbsms200 kbCollections kbInventory kbQuery kbsmsAdmin 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
