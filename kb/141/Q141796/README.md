---
layout: page
title: "Q141796: HOWTO: Identify the Jet Database Engine Components"
permalink: /kb/141/Q141796/
---

## Q141796: HOWTO: Identify the Jet Database Engine Components

{% raw %}

	Article: Q141796
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbfile kbJET kbMFC kbVBp400 kbVBp500 kbVBp600
	Last Modified: 13-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Jet is the default database engine for Visual Basic as well as other Microsoft
	applications such as Microsoft Access, Microsoft Excel, Project, and Microsoft
	Foundation Classes (MFC). Which version of Jet you are using can be unclear
	because Visual Basic and other applications using Jet are continually being
	updated. The tables and explanations in this article are intended to help you
	identify the version and components of Jet that you are using for the given
	application.
	
	MORE INFORMATION
	================
	
	The list below displays which version of Jet is shipped with each of the
	following products:
	
	Application                  Microsoft JET version
	----------------------------------------------------
	Microsoft Access 1.0             1.0
	Microsoft Access 1.1             1.1
	Microsoft Access 2.0             2.0
	Microsoft Access 2.0             2.5 with Microsoft Access Service Pack
	Microsoft Access 7.0             3.0
	Microsoft Access 97              3.5
	Visual Basic 3.0                 1.1
	Visual Basic 3.0                 2.0 with Visual Basic Compatibility Layer
	Visual Basic 3.0                 2.5 with Microsoft Access Service Pack
	Visual Basic 4.0 16-bit          2.5
	Visual Basic 4.0 32-bit          3.0
	Visual Basic 5.0 32-bit          3.5
	Microsoft Excel 7.0              3.0
	Microsoft Excel 97               3.5
	Microsoft Project                2.0
	Microsoft Foundation Classes     3.0
	
	Compatibility Among Versions
	----------------------------
	
	With each new version of Microsoft Jet, enhancements in functionality and changes
	to the structure of the database file cause problems with backward
	compatibility. Wherever possible, efforts have been made to ensure an easy
	migration path among versions. However, incompatibilities do exist. The
	following table illustrates how database files and objects can be used among
	different versions of Microsoft Jet.
	
	Jet Version
	                        1.0   1.1   2.0   2.5   3.0   3.5   3.51
	
	-----------------------------------------------------------------
	MDB Version      1.0     Y     Y     Y     Y     Y     Y     Y
	                1.1     N     Y     Y     Y     Y     Y     Y
	                2.0     N     N     Y     Y     Y     Y     Y
	                2.5     N     N     N     Y     Y     Y     Y
	                3.0     N     N     N     N     Y     Y     Y
	                3.5     N     N     N     N     N     Y     Y
	                3.51    N     N     N     N     N     N     Y
	
	A "Y" indicates that the database can be used without conversion; "N" indicates
	that the database cannot be used or converted. With DAO code you can open any
	version of any database up to the same version of Microsoft Jet. However,
	Microsoft Access can open only those databases with the same version as itself,
	but it can link to tables with the same or earlier version. In other words, if
	you upgrade to Microsoft Jet 3.0, you will still be able to read version 2.x
	databases.
	
	Notice that Visual Basic 3.0 is capable of using three different versions of Jet
	each requiring a separate set of dynamic link libraries (.dlls). This can cause
	problems when your Visual Basic application expects to use Jet 2.0 for example,
	and then another Visual Basic application using an earlier version of Jet gets
	installed on the same system replacing some of the version 2.0 .dlls with
	version 1.1. Typically the problem .dll in this situation is VBDB300.DLL because
	it determines which version of the Jet engine will be used.
	
	The following table should help you solve any version conflicts and help you
	identify the version of Jet you are using. You may use the Wps.exe utility
	shipped with Visual Basic to find out which version of Jet you currently have
	loaded in memory. Wps.exe is located in the \VB\CDK directory of Visual Basic
	3.0 Professional, and in \TOOLS\PSS directory of the Visual Basic 4.0 CD. Pay
	special attention to the version information obtained from File Manager (File,
	Properties) in Visual Basic 3.0, and Microsoft System Info. in Visual Basic 4.0
	32-bit.
	
	The following files are required by Visual Basic to use the Jet Database Engine:
	
	Jet Version    File          Version     Description
	--------------------------------------------------------------
	
	1.1            VBDB300.DLL   3.00.0528   VB/JET support
	              MSAES110.DLL  1.10.0000   Expression services
	              MSAJT110.DLL  1.10.0001   Jet 1.1 engine
	              XBS110.DLL    1.10.0002   External xBASE ISAM
	              BTRV110.DLL   1.10.0000   External Btrieve ISAM
	              PDX110.DLL    1.10.0000   External Paradox ISAM
	
	2.0 (comlyr)   VBDB300.DLL   3.00.0529   VB/JET support
	              MSAJT112.DLL  1.99.1605   Jet 2.x comp. loader
	              MSAJT200.DLL  2.00.0000   Jet 2.0 engine
	              XBS200.DLL    2.00.0000   External xBASE ISAM
	              BTRV200.DLL   2.00.0000   External Btrieve ISAM
	              PDX200.DLL    2.00.0000   External Paradox ISAM
	
	2.5 (accsvc)   VBDB300.DLL   3.00.0529   VB/JET support
	              MSAJT112.DLL  1.99.1605   Jet 2.x comp loader
	              MSAJT200.DLL  2.50.1606   Jet 2.5 engine
	              MSJETERR.DLL  2.50.1108   Error services
	              MSJETINT.DLL  2.50.1108   International
	              XBS200.DLL    2.50.1108   External xBASE ISAM
	              BTRV200.DLL   2.50.1108   External Btrieve ISAM
	              PDX200.DLL    2.50.1108   External Paradox ISAM
	
	2.5 (VB4 16)   VBDB16.DLL    4.00.2422   VB/JET support
	              MSAJT200.DLL  2.50.1606   Jet 2.5 engine
	              MSJETERR.DLL  2.50.1111   Error services
	              MSJETINT.DLL  2.50.1111   International
	              XBS200.DLL    2.50.1117   External xBASE ISAM
	              BTRV200.DLL   2.50.1117   External Btrieve ISAM
	              PDX200.DLL    2.50.1117   External Paradox ISAM
	              MSXL2016.DLL  2.50.1117   External Excel ISAM
	              MSTX2016.DLL  2.50.1117   External Text ISAM
	
	3.0            MSJT3032.DLL  3.0.0.2118  Jet 3.0 engine
	              MSJINT32.DLL  3.0.0.2118  International
	              MSJTER32.DLL  3.0.0.2118  Error services
	              MSXL3032.DLL  3.0.0.2001  External Excel ISAM
	              MSRD2X32.DLL  3.0.0.2118  External Jet 2.0 ISAM
	              MSLT3032.DLL  3.0.0.2008  External Lotus ISAM
	              MSPX3032.DLL  3.0.0.2001  External Paradox ISAM
	              MSXB3032.DLL  3.0.0.2008  External xBASE ISAM
	              MSTX3032.DLL  3.0.0.2008  External Text ISAM
	
	3.5            MSJET35.DLL   3.50.3602.4 Jet 3.5 engine
	              MSJTER35.DLL  3.50.3602.0 Error service
	              MSJINT35.DLL  3.50.3602.5 International
	              MSXBSE35.DLL  3.50.3428.0 External xBASE ISAM
	              MSEXCL35.DLL  3.50.3428.0 External Excel ISAM
	              MSTEXT35.DLL  3.50.3428.0 External Text ISAM
	              MSRD2X35.DLL  3.50.3602.0 External Jet 2.x ISAM
	              MSPDOX35.DLL  3.50.3428.0 External Paradox ISAM
	              MSLTUS35.DLL  3.50.3428.0 External Lotus ISAM
	
	3.51 (SR-1)    MSJET35.DLL   3.51.0623.4  Jet 3.51 engine
	              MSJTER35.DLL  3.51.0623.0  Error service
	              MSJINT35.DLL  3.51.0623.0  International
	              MSXBSE35.DLL  3.50.3907.0 External xBASE ISAM
	              MSEXCL35.DLL  3.50.3907.0 External Excel ISAM
	              MSTEXT35.DLL  3.50.3907.0 External Text ISAM
	              MSRD2X35.DLL  3.50.3907.0 External Jet 2.x ISAM
	              MSPDOX35.DLL  3.50.3907.0 External Paradox ISAM
	              MSLTUS35.DLL  3.50.3907.0 External Lotus ISAM
	
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  Comlyr.exe (Visual Basic Compatibility Layer)
	  (http://download.microsoft.com/download/access20/doc/1/WIN98/EN-US/Comlyr.exe)
	
	  Accsvc.exe (Microsoft Access Service Pack)
	  (http://download.microsoft.com/download/access20/SP/1/WIN98/EN-US/Accsvc.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	REFERENCES
	==========
	
	Microsoft Jet Database Engine Programmer's Guide, by Dan Haught and Jim
	Ferguson, Microsoft Press 1995 For additional information, please click the
	article numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q113683 FILE: Fact Sheet on Jet 2.0/VB 3.0 Compatibility Layer
	
	  Q122927 WX1124: Microsoft Access Version 2.0 Service Pack
	
	
	  Q172733 Updated Version of Microsoft Jet 3.5 Available on MSL
	
	
	Additional query words: Comlyr Accsvc
	
	======================================================================
	Keywords          : kbfile kbJET kbMFC kbVBp400 kbVBp500 kbVBp600 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600 kbVB400Search kbVB400 kbVB16bitSearch
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
