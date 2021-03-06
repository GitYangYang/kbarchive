---
layout: page
title: "Q257364: SMS: French Security: Wuser32.exe Has Everyone Full Control"
permalink: /kb/257/Q257364/
---

## Q257364: SMS: French Security: Wuser32.exe Has Everyone Full Control

{% raw %}

	Article: Q257364
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbSecurity kbsms120 kbsms120bug kbHelpDesk KbSECVulnerability
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If the Systems Management Server (SMS) 2.0 Remote Control feature is installed
	and enabled on a computer, the folder in which the Remote Control agent is
	located has its permissions set to Everyone Full Control by default. If a
	malicious user were to replace the client code with other code, the code would
	run automatically in a System context the next time that user rebooted the
	computer and logged on. This vulnerability exists only if the Remote Control
	feature is enabled; no other SMS features are affected by it.
	
	CAUSE
	=====
	
	The client code for the Remote Control agent runs in the highly privileged
	System security context. However, it is installed in a folder that by default
	allows any user who can interactively log on to the computer to have complete
	access to the folder.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Apply it only to
	computers that are experiencing this specific problem. This fix may receive
	additional testing. Therefore, if you are not severely affected by this problem,
	Microsoft recommends that you wait for the next Systems Management Server
	service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The typical support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The French version of this fix should have the following file attributes or
	later:
	
	  Date         Time   Version         Size    File name   Platform
	  ----------------------------------------------------------------
	  01/04/2000  03:16a                   67     Compver.ini   
	  03/28/2000  04:32p  2.0.1380.1108  1.61 MB  Remctrl.exe   Intel
	  03/28/2000  04:44p  2.0.1380.1108  1.23 MB  Remctrl.exe   Alpha
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	MORE INFORMATION
	================
	
	To install the hotfix, use the appropriate method.
	
	Method 1: Using the Hotfix Installer
	------------------------------------
	
	1. Create a folder in a location that is accessible to your SMS site server.
	
	2. Copy the Q257364.exe file and platform folders to the new folder. The folder
	  structure must be such that the program file is located one folder "above"
	  the platform folders.
	
	3. Log on to your site server by using an account with administrative
	  privileges.
	
	4. From each of the primary and secondary SMS site servers in your environment,
	  run the program file (Q257364.exe).
	
	5. Finish any necessary installation steps as instructed by the installation
	  program.
	
	NOTE: You can run the Q257364.exe file using the /s command-line switch.
	
	Method 2: Manual Installation
	-----------------------------
	
	1. Copy the updated SMS files to a disk or network share that is accessible from
	  the SMS site server you want to update.
	
	2. Quit the SMS Administrator console and stop all SMS services by using Control
	  Panel. If the SMS_SITE_BACKUP service is running, stop it also.
	
	3. Copy the Remctrl.exe file from the appropriate <Platform> subfolder to
	  the <Driveletter>:\Sms\Inboxes\Clicomp.src\Remctrl\<Platform>
	  folder.
	
	4. Replace the Compver.ini file in the
	  <Driveletter>:\Sms\Inboxes\Clicomp.src\Remctrl folder with the
	  Compver.ini file from the hotfix bundle source folder.
	
	5. Restart the SMS site services.
	
	The new files are replicated to all logon points and Client Access Points (CAPs).
	After all logon points and CAPs are updated, allow an additional 23 hours for
	clients to begin their update polling cycle.
	
	After applying the patch, the permissions on the
	<SMS_local_dir>\MS\SMS\Clicomp\Remctrl folder should be:
	
	  Administrators: Full Access
	  Everyone: Read, Execute
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbSecurity kbsms120 kbsms120bug kbHelpDesk KbSECVulnerability 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
