---
layout: page
title: "Q240840: Operator Started CPIC/APPC Application May Cause Events 60 and 7"
permalink: /kb/240/Q240840/
---

## Q240840: Operator Started CPIC/APPC Application May Cause Events 60 and 7

{% raw %}

	Article: Q240840
	Product(s): Microsoft SNA Server
	Version(s): 4.0 SP2
	Operating System(s): 
	Keyword(s): kbsna400sp2kbbuglist
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 4.0 SP2 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	Events 60 and 703 may be logged and a negative response to an FMH-5 Attach
	Message may be sent with a sense code of 084C0000 (transaction program not
	available, no retry).
	
	CAUSE
	=====
	
	An operator-started transaction program (TP) may have registry entries defining
	it as an auto-started invokable TP running as a service and/or as an
	application. This causes two or more entries in the SNA Server service table
	with the same TP name. When an FMH-5 Attach message is sent to start a
	conversation with the TP, the DMOD process should search the SNA Server service
	table using the following priority order:
	
	  1. Operator-started TPs currently running locally
	  2. Operator-started TPs currently running on another computer
	  3. Auto-started (invokable) TPs running locally
	  4. Auto-started (invokable) TPs on another computer
	
	SNA Server 4.0 Service Pack 2 may route an incoming Attach message to an
	auto-started TP even though an operator-started TP exists and is located by the
	DMOD. If the auto-started TP is configured to run the same application as the
	operator-started TP, the TP should execute successfully. If the auto-started TP
	is not correctly configured or is configured to run a different program than the
	operator-started TP, the incoming Attach message may fail with the symptoms
	described earlier or may result in some other error.
	
	WORKAROUND
	==========
	
	Operator-started transaction programs do not require registry entries defining
	them as auto-started invokable transaction programs to an SNA Server computer.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To stop the errors from occurring, delete the registry entries for the
	operator-started invokable transaction program.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server 4.0 Service Pack 2.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna400sp2 kbbuglist
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400SP2
	Version           : :4.0 SP2
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
