---
layout: page
title: "Q185282: PRB: CRichEditView, AppWizard View-Based Apps and Compound Files"
permalink: /kb/185/Q185282/
---

## Q185282: PRB: CRichEditView, AppWizard View-Based Apps and Compound Files

{% raw %}

	Article: Q185282
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.0,4.1,4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbole kbCodeGen kbDocView kbMFC kbVC400 kbVC500 kbVC600 kbDSupport kbGrpDSMFCATL
	Last Modified: 17-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You can experience two problems when you choose compound file support for an MFC
	application based on CRichEditView. The first problem also occurs with MFC
	applications based on other view classes (eg. CView, CEditView, and so on):
	
	1. The document's Serialize function will pass in what seems to be an invalid
	  CArchive object. For example, if you place the following code in the
	  Serialize function of an application that includes compound file support,
	  nothing will appear in the message box:
	
	        CFile *pFile = ar.GetFile();
	        AfxMessageBox(pFile->GetFilePath());
	
	2. When you save your document to a file, Word or WordPad will not be able to
	  correctly read it.
	
	These problems can arise when you use the AppWizard to create single document
	interface (SDI) or multiple document interface (MDI) applications, and when you
	enable compound file support (in Step 3 of the AppWizard). Typically, you see a
	call to EnableCompoundFile() in the constructor of your CDocument-derived class
	when this problem occurs.
	
	CAUSE
	=====
	
	1. The CArchive object passed in by the document's Serialize function is fine.
	  The m_strFileName (file name) member of CArchive is empty because the
	  compound file support is enabled in the application. The CArchive object is
	  associated with a COleStreamFile object, which is a wrapper for a stream
	  object (it supports the IStream interface). This stream object represents
	  only a part of the compound file, and so the file name field is empty.
	
	2. When you enable compound files in a CrichEditView-based application, the Rich
	  Text Format (RTF) stream provided is stored in a compound file layout, which
	  neither Word nor WordPad understands. When you try to display a compound file
	  with either Word or Wordpad, the files display as plain text.
	
	RESOLUTION
	==========
	
	1. If you want to use compound files, your code must not try to get information
	  that isn't defined for a compound file from the CArchive object.
	
	2. If you want your files to be compatible with Word and WordPad, don't choose
	  compound file support. Word and WordPad can understand the RTF stream stored
	  in a flat file.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	To reproduce the perceived problem of an invalid CArchive object, perform the
	following steps:
	
	1. Use the MFC AppWizard (exe) to generate an SDI or MDI application with all
	  the defaults, except in Step 3.
	
	  In Step 3, select any of the following options: Container, Mini-server,
	  Full-server, or Both container and server. Then select "Yes" in response to
	  "Would you like support for compound files?".
	
	2. Finish AppWizard, and put a break point at the beginning of the document's
	  Serialize function.
	
	3. Build a debug version. Run the application, and save a file.
	
	4. At the breakpoint, do a QuickWatch of the ar (CArchive) object. Notice that
	  ar.m_strFileName is empty. The same thing occurs when opening a file.
	
	REFERENCES
	==========
	
	Visual C++ Programmer's Guide: Adding Program Functionality; Details;
	Containers: Compound Files.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q166769 PRB: MFC ActiveX Document Servers Require Compound File Support
	
	Additional query words:
	
	======================================================================
	Keywords          : kbole kbCodeGen kbDocView kbMFC kbVC400 kbVC500 kbVC600 kbDSupport kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:4.0,4.1,4.2,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
