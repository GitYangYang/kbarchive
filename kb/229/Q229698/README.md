---
layout: page
title: "Q229698: SMS: New Functionality Added to Audit"
permalink: /kb/229/Q229698/
---

## Q229698: SMS: New Functionality Added to Audit

{% raw %}

	Article: Q229698
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbsms120 kbsms120bug
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A hotfix for Audit is now available that has three new command-line arguments:
	
	- /mif
	
	- /noidmif
	
	- /notime
	
	Each of these new arguments is described below.
	
	/mif
	----
	
	Instructs Audit to use a .mif file name extension instead of the default .nhm
	extension. This is useful if you want the Inventory Processor to create
	DeltaMIFs rather than the full MIFs created when No History MIFs (NHM) are
	processed.
	
	/noidmif
	--------
	
	Instructs Audit to create a NOIDMIF called Audit.mif that is placed in the
	client's local \Noidmifs directory. Please note that NOIDMIFs are collected by
	the Inventory Agents during a full inventory, so the collection of the Audit.mif
	will only occur when inventory is taken.
	
	/notime
	-------
	
	Instructs Audit to create a MIF that does not report time (that is, only the
	file's date is reported). The /notime argument can be used with the default
	Audit (NHM) or in conjunction with the /mif and/or /noidmif parameters as well.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Systems Management Server service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time                Size      File name    Platform
	  -------------------------------------------------------------
	
	  4/19/99   8:33pm            135,216    Audit16.exe   x86
	  4/15/99   7:43pm            189,936    Audit32.exe   x86
	  4/15/99   7:44pm            629,008    Audit32.exe   Alpha
	  4/15/99   7:46pm              5,552   Auditstr.dll   x86
	  4/15/99   7:51pm              5,904   Aud32str.dll   x86
	  4/15/99   7:42pm              5,904   Aud32str.dll   Alpha 
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2.
	
	MORE INFORMATION
	================
	
	To install the hotfix, perform the following steps on the Systems Management
	Server site server:
	
	1. Replace the Audit32.exe file in the
	  <SMS_root>\Primsite.srv\Audit\Package\<Platform>.bin directory
	  with the hotfixed version.
	
	2. Replace the Aud32str.dll file in the
	  <SMS_root>\Primsite.srv\Audit\Package\<Platform>.bin\00000409
	  directory with the hotfixed version.
	
	3. Replace the Audit16.exe file in the
	  <SMS_root>\Primsite.srv\Audit\Package\X86.bin directory with the
	  hotfixed version.
	
	4. Replace the Auditstr.dll file in the
	  <SMS_root>\Primsite.srv\Audit\Package\X86.bin\00000409 directory with
	  the hotfixed version.
	
	NOTE: You can perform these steps automatically by using Hotfix.exe with the
	provided Hotfix.ini file.
	
	Any previous Audit packages that have been distributed will need to be
	refreshed.
	
	WARNING: Before switching from using the default NHM to either a MIF or NOIDMIF,
	you should fully understand how each MIF will affect your Systems Management
	Server system and database. Please see the Systems Management Server SDK for
	more information on MIFs.
	
	Additional query words: prodsms arg args argument parameter parameters param parm params parms
	
	======================================================================
	Keywords          : kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
