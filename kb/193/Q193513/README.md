---
layout: page
title: "Q193513: BUG: Breakpoints Not Hit in ATL MMC Snap-In"
permalink: /kb/193/Q193513/
---

## Q193513: BUG: Breakpoints Not Hit in ATL MMC Snap-In

{% raw %}

	Article: Q193513
	Product(s): Microsoft C Compiler
	Version(s): 3.0,6.0
	Operating System(s): 
	Keyword(s): kbDebug kbVC600bug kbATL300 kbATL300bug kbFAQ kbGrpDSTools kbNoUpdate
	Last Modified: 12-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Active Template Library (ATL) 3.0, used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - The Integrated Debugger 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The debugger may not break on your breakpoints when you try to debug an ATL MMC
	(Microsoft Management Console) Snap-In on a Windows NT 4.0 machine.
	
	CAUSE
	=====
	
	The ATL Object Wizard adds code that registers objects differently. The About
	object uses the DECLARE_REGISTRY() macro for registering itself. Other objects
	in the same Snap-In use an .rgs file. As a result, the About object is
	registered using a long file name (in the InprocServer32 key). Other objects are
	registered with a short file name.
	
	MMC first creates the About object and loads the DLL with the long file name.
	When other objects are created by MMC, the DLL is reloaded in a different memory
	location with the short file name. Debugger breakpoints (int 3 instructions) are
	inserted in the context of the first DLL, so any code executed in the context of
	the second DLL won't have any int 3 instructions, and therefore breakpoints are
	not hit.
	
	RESOLUTION
	==========
	
	You can use one of the following four workarounds:
	
	- 
	
	  Workaround 1
	  ------------
	
	  Use a directory and project name that does not use long file names.
	
	- 
	
	  Workaround 2
	  ------------
	
	  Change the About object to use the .rgs file as shown below:
	
	  1. Create a new registry file and edit it as follows (replacing the CLSID and
	     class name):
	
	        HKCR
	         {
	            MyClassAbout.1 = s 'MyClassAbout Class'
	            {
	               CLSID = s '{22A88065-391D-11D2-8164-00C04F7948A7}'
	               CurVer = s 'MyClassAbout.1'
	            }
	            NoRemove CLSID
	            {
	               ForceRemove
	         {22A88065-391D-11D2-8164-00C04F7948A7} = s 'MyClassAbout Class'
	               {
	                  ProgID = s 'MyClassAbout.1'
	                  VersionIndependentProgID = s 'MyClassAbout.1'
	                  ForceRemove 'Programmable'
	                  InprocServer32 = s '%MODULE%'
	                  {
	                     val ThreadingModel = s 'Both'
	                  }
	               }
	            }
	         }
	
	  2. Save the new registry file as MyClassAbout.rgs and import this file into
	     your project resource. Change its id to IDR_MYCLASSABOUT.
	
	  3. Replace the DECLARE_REGISTRY line in the About class with the following:
	
	  DECLARE_REGISTRY_RESOURCEID(IDR_MYCLASSABOUT)
	
	  4. Rebuild all.
	
	- 
	
	  Workaround 3
	  ------------
	
	  Unregister the DLL and comment out the object entry for the About object when
	  debugging.
	
	- 
	
	  Workaround 4
	  ------------
	
	  Use _asm int 3 or DebugBreak or ATLASSERT(0) to break into the debugger and
	  set/re-enable your break points.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words: snapin
	
	======================================================================
	Keywords          : kbDebug kbVC600bug kbATL300 kbATL300bug kbFAQ kbGrpDSTools kbNoUpdate 
	Technology        : kbVCsearch kbAudDeveloper kbATLsearch
	Version           : :3.0,6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
