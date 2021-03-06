---
layout: page
title: "Q168449: PRB: Use of Data-Bound Controls Is Version Dependent"
permalink: /kb/168/Q168449/
---

## Q168449: PRB: Use of Data-Bound Controls Is Version Dependent

{% raw %}

	Article: Q168449
	Product(s): Microsoft C Compiler
	Version(s): 4.2 4.20b 5.0
	Operating System(s): 
	Keyword(s): kbDAOsearch kbDatabase kbMFC kbODBC kbVC kbVC420 kbVC500 kbprb
	Last Modified: 17-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 5.0, 4.2b 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 5.0, 4.2b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Loading Visual C++ 5.0 on a system that has Visual C++ 4.x installed will cause
	numerous DLLs, OCXs, and other components to be overwritten. One set of
	components that is updated are the data-bound controls.
	
	- DBGrid
	- DBListBox
	- DBComboBox
	- Remote Data Control
	
	Although it is possible to load Visual C++ 4.x and 5.0 on the same system in
	different directories, Visual C++ 4.x will have trouble displaying the
	data-bound controls properties.
	
	Displaying the "All" Tab on Database Controls such as Microsoft Data Combo and
	Microsoft Masked Edit Box shows <Property unknown> after having installed
	Visual C++ 5.0. Normally, you will see Datasource, field properties, etc.
	
	CAUSE
	=====
	
	Visual C++ 5.0 installs upgrades of the data-bound controls that have the same
	file names as the versions that ship with Visual C++ 4.x.
	
	RESOLUTION
	==========
	
	If you want to work with Visual C++ 4.2, replace the appropriate controls in
	your system32 from the version 4.2 redist\ocx directory (in this case,
	MSMASK32.OCX DBLIST32.OCX).
	
	The Property Dialog Headings for these controls have also changed to Microsoft
	DBCombo, version 5.0 and Microsoft Masked Edit Box version 5, rather than
	Microsoft DBCombo and Microsoft Masked Edit Box. Creating a new project exhibits
	the same problem. This makes is somewhat difficult to use these controls.
	
	There are three controls that have the same name as the previous version and
	therefore overwrite the version that works with version 4.2:
	
	- DBGrid32.ocx
	- DBList32.ocx
	- MSMask32.ocx
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	It is not possible to work with version 5.0 data-bound controls in Visual C++
	4.x or with version 4.x data-bound controls in Visual C++ 5.0. The data-bound
	controls have been changed in these two versions.
	
	It is highly recommended that you chose between versions 4.2 or 5.0 when working
	with database applications that use the data-bound controls.
	
	Although this is problem in the design interface, the newer 5.0 controls can be
	used by older 4.2 applications at run time.
	
	REFERENCES
	==========
	
	Vcread.htm that ships with Visual C++ 5.0
	
	Additional query words: run-time
	
	======================================================================
	Keywords          : kbDAOsearch kbDatabase kbMFC kbODBC kbVC kbVC420 kbVC500 kbprb 
	Technology        : kbVCsearch kbAudDeveloper kbVC420 kbVC500 kbVC32bitSearch kbVC420b kbVC500Search
	Version           : 4.2 4.20b 5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
