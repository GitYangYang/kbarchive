---
layout: page
title: "Q244409: Access Account Security on Distribution Points May Be Incorrect"
permalink: /kb/244/Q244409/
---

## Q244409: Access Account Security on Distribution Points May Be Incorrect

{% raw %}

	Article: Q244409
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbSoftwareDist kbsms200sp2fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In a multiple-domain environment, package security may be applied incorrectly on
	distribution points. Specifically, the NTFS permissions of the package folder
	are set to a local group rather than the intended global group from a trusted
	domain, even though the account was properly prefixed when it was added by using
	the SMS Administrator console. This problem occurs only if there is a group with
	the same name in the domain in which the distribution point resides. For
	example:
	
	A Systems Management Server (SMS) administrator defines AccountDomain\TestGroup
	under Access Accounts. The targeted distribution server is a part of a domain
	named ResourceDomain, which trusts AccountDomain. The ResourceDomain domain also
	contains a group named TestGroup. Distribution Manager adds permissions to the
	distribution point using the TestGroup group from the ResourceDomain domain,
	instead of TestGroup from AccountDomain. However, if TestGroup does not exist in
	the ResourceDomain domain, Distribution Manager adds permissions using
	AccountDomain\TestGroup.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, click the following article
	number to view the article in the Microsoft Knowledge Base:
	
	  Q236325 How to Obtain the Latest Systems Management Server 2.0 Service Pack
	
	
	
	WORKAROUND
	==========
	
	To work around this problem, use any of the following methods:
	
	- Use unique user group names that do not exist in other domains.
	
	- If the intended user group is a global group and the same-named user group is
	  a local group, add the global group to the local group of the appropriate
	  domain.
	
	- Apply permissions to distribution points manually after Distribution Manager
	  finishes its process.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0. This problem was first corrected in Systems Management Server
	version 2.0 Service Pack 2.
	
	MORE INFORMATION
	================
	
	To install the hotfix, perform the following steps at the SMS site server:
	
	1. Stop the SMS_EXECUTIVE and SMS_SITE_COMPONENT_MANAGER services.
	
	2. Replace the Ccmcore.exe file in the
	  <SMS_root>\Inboxes\Clicomp.src\Base\<Platform> folder with the
	  version obtained from the hotfix.
	
	3. Replace the Clicore.exe file in the
	  <SMS_root>\Inboxes\Clicomp.src\Base\<Platform> folder with the
	  version obtained from the hotfix.
	
	4. Replace the Compver.ini file in the <SMS_root>\Inboxes\Clicomp.src\Base
	  folder with the version obtained from the hotfix.
	
	5. Replace the Abnwcli.dll file in the <SMS_root>\Bin\<Platform>
	  folder with the version obtained from the hotfix.
	
	6. Replace the Ccim32.dll file in the <SMS_root>\Bin\<Platform>
	  folder with the version obtained from the hotfix.
	
	7. Replace the Falclin.dll file in the <SMS_root>\Bin\<Platform>
	  folder with the version obtained from the hotfix.
	
	8. Replace the Mslmclin.dll file in the <SMS_root>\Bin\<Platform>
	  folder with the version obtained from the hotfix.
	
	9. Replace the Mslmsvrn.dll file in the <SMS_root>\Bin\<Platform>
	  folder with the version obtained from the hotfix.
	
	10. Start the SMS_EXECUTIVE and SMS_SITE_COMPONENT_MANAGER services.
	
	11. Allow the updated Compver.ini, Clicore.exe, and Ccmcore.exe files to be
	  propagated to all Logon Points and/or Client Access Points (CAPS) in the
	  site.
	
	NOTE: The default Client Configuration Installation Manager (CCIM) Polling
	interval is 23 hours. Therefore, it may take up to 23 hours for the hotfix files
	to be propagated to the clients. To speed up this process, use any of the
	following methods:
	
	- Stop and restart the SMS Client service on each client. For Microsoft Windows
	  NT, stop and restart the service. For Microsoft Windows 95 or Microsoft
	  Windows 98, a restart is required.
	
	- Create a software distribution for one of the Resource Kit tools (Setevnt.exe
	  or Cliutils.exe), along with the appropriate parameters to start a CCIM work
	  cycle. The tools are located on Systems Management Server (SMS) 2.0 CD-ROM.
	
	  For Setevnt.exe, the syntax is:
	
	  setevnt /q
	
	For Cliutils.exe, the syntax is:
	
	  Cliutils KICK "Client Configuration Installation Manager"
	
	- If you have the Networking Logon Client Installation option enabled, have
	  users log off and back on.
	
	- Have users run SMSMan manually.
	
	NOTE: Windows 95/98 clients may require a restart after the hotfix files have
	been installed to receive full hotfix functionality. To verify this, review the
	Clicore.log file after the update. If a restart is required, the entry listed
	below is logged. Because of the nature of this hotfix, Microsoft recommends that
	a mandatory restart policy be used for all Windows 95-based and Windows 98-based
	computers after the hotfix has been applied.
	
	  Reboot required - disabling component until reboot
	
	WARNING: This hotfix contains files for the SMS Client Base component that have a
	version of 2.00.1380.1056. Before applying this hotfix, you should verify that
	your current SMS Client Base component version is earlier than 2.00.1380.1056.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbSoftwareDist kbsms200sp2fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
