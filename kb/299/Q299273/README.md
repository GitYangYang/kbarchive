---
layout: page
title: "Q299273: UPN Logon Option Does Not Work After You Apply Fix from MS01-026"
permalink: /kb/299/Q299273/
---

## Q299273: UPN Logon Option Does Not Work After You Apply Fix from MS01-026

{% raw %}

	Article: Q299273
	Product(s): Internet Information Server
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): kbCOMIS kbWin2000PreSP3Fix kbWin2000sp3fix
	Last Modified: 15-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A user principal name (UPN) logon option, which is documented in Microsoft
	Knowledge Base articles Q260269 and Q168908, does not work after you apply the
	fix from the Microsoft security bulletin MS01-026. The Microsoft security
	bulletin MS01-026 fix is referenced in Microsoft Knowledge Base article Q293826
	and is available from the following Microsoft Web site:
	
	  http://www.microsoft.com/technet/security/bulletin/ms01-026.asp
	
	After you apply the Microsoft security bulletin MS01-026 fix, users must
	explicitly specify the logon domain.
	
	CAUSE
	=====
	
	This problem occurs because DefaultLogonDomain parameter of backslash ("\") from
	Q168908 is no longer honored.
	
	RESOLUTION
	==========
	
	For IIS 5.0:
	
	To resolve this problem, obtain the latest service pack for Windows 2000. For
	additional information, click the following article number to view the article
	in the Microsoft Knowledge Base:
	
	  Q260910 How to Obtain the Latest Windows 2000 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date        Time    Version      Size    File name
	  --------------------------------------------------
	  05/25/2001 17:10  5.0.2195.35   332,560  Asp.dll      
	  05/25/2001 17:10  5.0.2195.36    13,584  Infoadmn.dll    
	  05/25/2001 17:10  5.0.2195.36   245,520  Infocomm.dll    
	  05/25/2001 17:10  5.0.2195.36    62,736  Isatq.dll       
	  05/25/2001 17:10  5.0.2195.35     7,440  W3ctrs.dll      
	
	
	For IIS 4.0:
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Apply it only to
	computers that are experiencing this specific problem. This fix may receive
	additional testing. Therefore, if you are not severely affected by this problem,
	Microsoft recommends that you wait for the next Microsoft Windows NT service
	pack that contains this fix.
	
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
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date         Time   Version    Size   File name
	  --------------------------------------------------------------
	  07-Jun-2001  20:09  4.2.766.1  214,544  Adsiis.dll
	  07-Jun-2001  20:09  4.2.766.1  330,672  Asp.dll
	  07-Jun-2001  20:08  4.2.766.1   55,392  Httpodbc.dll
	  07-Jun-2001  20:09  4.2.766.1   98,912  Iischema.dll
	  07-Jun-2001  20:07  4.2.766.1   63,472  Iislog.dll
	  07-Jun-2001  20:07  4.2.766.1  185,792  Infocomm.dll
	  07-Jun-2001  20:07  4.2.766.1   29,520  Iscomlog.dll
	  17-Sep-1998  19:26                 992  Rmiisupd.cmd
	  07-Jun-2001  20:08  4.2.766.1   38,256  Ssinc.dll
	  07-Jun-2001  20:08  4.2.766.1   25,360  Sspifilt.dll
	  07-Jun-2001  20:08  4.2.766.1  229,536  W3svc.dll
	  07-Jun-2001  20:08  4.2.766.1   88,032  Wam.dll
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Internet Information
	Services 5.0. This problem was first corrected in Windows 2000 Service Pack 3.
	
	MORE INFORMATION
	================
	
	NOTE: This problem will also occur after installing the Windows NT 4.0 SRP since
	it contains MS01-026.
	
	For additional information about how to obtain a hotfix for Windows 2000
	Datacenter Server, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q265173 The Datacenter Program and Windows 2000 Datacenter Server Product
	
	For additional information about how to install multiple hotfixes with only one
	reboot, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q296861 Use QChain.exe to Install Multiple Hotfixes with One Reboot
	
	For additional information about how to install Windows 2000 and Windows 2000
	hotfixes at the same time, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q249149 Installing Microsoft Windows 2000 and Windows 2000 Hotfixes
	
	Additional query words: kbIISCom
	
	======================================================================
	Keywords          : kbCOMIS kbWin2000PreSP3Fix kbWin2000sp3fix 
	Technology        : kbiisSearch kbiis500 kbiis400
	Version           : :4.0,5.0
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
