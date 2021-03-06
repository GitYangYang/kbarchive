---
layout: page
title: "Q195113: XCLN: Problem Opening Attachments with Netscape Navigator"
permalink: /kb/195/Q195113/
---

## Q195113: XCLN: Problem Opening Attachments with Netscape Navigator

{% raw %}

	Article: Q195113
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5,5.5 SP1,5.5 SP2
	Operating System(s): 
	Keyword(s): exc55 exc55sp1 exc55sp2
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2 
	-------------------------------------------------------------------------------
	
	
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	If you use Netscape Navigator 3.x or 4.05 to check e-mail messages on Exchange
	Server computers, Navigator is unable to open attachments. When you attempt to
	open the attachment, a Save As dialog box appears. Your only option is to save
	the file and open it later.
	
	CAUSE
	=====
	
	Although Internet Explorer can open attachments properly based on file
	extensions, Netscape Navigator requires that the correct content type be
	specified. If the server does not have the association of the content type with
	an extension in the registry, then Navigator does not get this information. An
	example of the association in the registry is .DOC = application/msword.
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	For problems with Microsoft Word document attachments, ensure that the following
	registry subkey and value exist:
	
	  HKEY_CLASSES_ROOT\.doc
	
	  Value Name: Content Type
	  Value Data: application/msword
	
	Because the problem is not specific to attachments with the .doc extension, you
	need to ensure that other extension types are defined in the following subkey:
	
	  HKEY_CLASSES_ROOT \<extension type>
	
	After you add the value above, you need to restart your computer. Stopping and
	restarting the Exchange Server services and Web services does not work.
	
	Failure to restart results in ASP 0115 errors in the client after the change has
	been made in the registry.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Exchange Server
	version 5.5.
	
	
	
	Additional query words: OWA
	
	======================================================================
	Keywords          : exc55 exc55sp1 exc55sp2 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2
	Version           : winnt:5.5,5.5 SP1,5.5 SP2
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
