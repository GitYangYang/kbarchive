---
layout: page
title: "Q243342: IISSYNC Returns a Status of 214598801"
permalink: /kb/243/Q243342/
---

## Q243342: IISSYNC Returns a Status of 214598801

{% raw %}

	Article: Q243342
	Product(s): Internet Information Server
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-AUG-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	- Microsoft Cluster Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run the IISSYNC utility to synchronize the IIS 4.0 settings between
	nodes on a computer running Microsoft Cluster Server version 1.0, IISSYNC
	returns a status of 214598801.
	
	Error number 214598801 refers to the following error:
	
	  (80110411 = The component's CLSID is missing or corrupt.)
	
	CAUSE
	=====
	
	A component in the Transaction Server IIS In-Process Applications Package does
	not have a corresponding AppWamClsid value in the IIS metabase.
	
	RESOLUTION
	==========
	
	Use the following steps to resolve this issue:
	
	1. Output the contents of the W3SVC key in the metabase to a file. To do this,
	  use the Mdutil.exe utility. This utility file is located on the Windows NT
	  Option Pack CD. Copy the Mdutil.exe file to the Inetsrv directory on your
	  primary Web server node, and then type the following:
	
	  mdutil enum_all w3svc > output.txt
	
	2. Print the Output.txt file.
	
	3. Search through the Output.txt file for the AppPackageID Clsid String metabase
	  entry. Take note of the CLSID set for the AppPackageID, because it is needed
	  in the next step. The AppPackageID will look similar to the following:
	
	  AppPackageID :[W] (STRING) "{3D14228C-FBE1-11d0-995D-00C04FD919C1}
	
	4. Output the Transaction Server IIS In-Process Applications Package Key from
	  the registry. To do this, open the Registry Editor, and then locate the
	  following key:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Transaction
	  Server\Packages\<AppPackageID Clsid String>
	
	  From the Registry menu, choose Save Subtree As. Type the file name
	  "Packages.Txt" (without the quotation marks), change the Save as Type to
	  Text, and then click Save.
	
	5. In the Output.txt file, scan through and look for entries named AppWamClsid.
	  Highlight each of these AppWamClsid entries. The AppWamClsid will look
	  similar to the following:
	
	  AppWamClsid :[IW] (STRING) "{60735342-438C-11D4-A35F-00C04F765674}"
	
	  Note: Each Web site and virtual or physical directory that is configured as an
	  application in the Internet Service Manager will have a unique AppWamClsid
	  associated with it.
	
	6. Take each AppWamClsid string you find in the Output.txt file and compare them
	  one at a time against the contents of the Packages.txt file. Each component
	  listed in the Packages.txt files has three entries for each individual
	  AppWamClsid. For example, if you have an AppWamClsid similar to the one shown
	  in the item above {60735342-438C-11D4-A35F-00C04F765674}, then there will be
	  three entries in the Packages.txt file that would look as follows:
	
	  Key Name: SOFTWARE\Microsoft\Transaction
	  Server\Packages\{3D14228C-FBE1-11d0-995D-00C04FD919C1}\Components\{60735342-438C-11D4-A35F-00C04F765674}\Interfaces
	  Class Name: <NO CLASS>
	  Last Write Time: 6/16/00 - 10:13 AM
	
	  Key Name: SOFTWARE\Microsoft\Transaction
	  Server\Packages\{3D14228C-FBE1-11d0-995D-00C04FD919C1}\Components\{60735342-438C-11D4-A35F-00C04F765674}\RoleMembership
	  Class Name: <NO CLASS>
	  Last Write Time: 6/16/00 - 10:13 AM
	
	  Key Name: SOFTWARE\Microsoft\Transaction
	  Server\Packages\{3D14228C-FBE1-11d0-995D-00C04FD919C1}\Components\{6073535D-438C-11D4-A35F-00C04F765674}
	  Class Name: <NO CLASS>
	  Last Write Time: 6/16/00 - 10:38 AM
	
	  Value 0
	  Name: Authentication
	  Type: REG_DWORD
	  Data: 0x4
	
	  Value 1
	  Name: SecurityEnabled
	  Type: REG_SZ
	  Data: Y
	
	7. Cross out the three entries in the Packages.txt file associated with each
	  individual AppWamClsid that you highlighted in the Output.txt file. When you
	  finish eliminating the individual AppWamClsids from the Packages.txt file,
	  the remaining entry, or possibly remaining entries, left in the Packages.txt
	  file are component entries in Transaction Server that do not have
	  corresponding application entries in the metabase.
	
	Now that you have determined which component CLSID does not have a matching
	AppWamClsid entry in the metabase, you can use the following steps to properly
	delete the component from Transaction Server, so that you can get a successful
	synchronization using IISSYNC.
	
	1. Determine the components ProgID name based on the CLSID. To do this, locate
	  the following key in the registry:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Transaction
	  Server\Components\<Offending Component Clsid String>
	
	2. There is a registry value labeled ProgID that has an entry with a descriptive
	  name. Write down that name. For example:
	
	  ProgID:REG_SZ:IISWAM6_ROOT_MY-VDIR
	
	3. To delete the IISWAM6_ROOT_MY-VDIR Component from Transaction Server, do the
	  following:
	
	  a. Open the Internet Service Manager.
	
	  b. Double-click Microsoft Transaction Server.
	
	  c. Double-click the Computers folder.
	
	  d. Double-click My Computer.
	
	  e. Double-click the Packages Installed folder.
	
	  f. Double-click the IIS In-Process Applications Package.
	
	  g. Double-click the Components folder.
	
	  h. In the list of all the Transaction Server Components (Web Applications)
	     currently configured to run In-Process in IIS, you will find the ProgID
	     name of the offending component, which you previously isolated. Highlight
	     the ProgID name you want to delete. Right-click the ProgID name and choose
	     Delete.
	
	  i. In the Confirm Item Delete window choose "YES."
	
	  Note: If there are multiple components without matching AppWamClsids, repeat
	  this step to delete each one.
	
	At this point, each AppWamClsid should have a corresponding Transaction Server
	IIS In-Process Applications Component ID and each Transaction Server IIS
	In-Process Applications Component should have a matching AppWamClsid.
	
	Additional query words: IIS 4.0 Cluster Server MSCS 1.0
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbAudDeveloper kbClustServSearch kbiis400
	Version           : winnt:4.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
