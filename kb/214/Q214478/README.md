---
layout: page
title: "Q214478: HOWTO: Handle Check Notifications in CCheckListBox"
permalink: /kb/214/Q214478/
---

## Q214478: HOWTO: Handle Check Notifications in CCheckListBox

{% raw %}

	Article: Q214478
	Product(s): Microsoft C Compiler
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbCtrl kbListBox kbMFC kbVC500 kbVC600 kbGrpDSMFCATL
	Last Modified: 26-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), included with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - Microsoft Visual C++.NET (2002) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	NOTE: Microsoft Visual C++ .NET (2002) supports both the managed code model that
	is provided by the Microsoft .NET Framework and the unmanaged native Microsoft
	Windows code model. The information in this article applies to unmanaged Visual
	C++ code only.
	
	The CCheckListBox check event can be handled through the undocumented
	CLBN_CHKCHANGE notification message.
	
	MORE INFORMATION
	================
	
	CCheckListBox is an MFC control based on an owner drawn ListBox control. It
	consists of a list of items with a check box. An item can be selected by
	clicking inside the check box next to the text of the item. This generates a
	CLBN_CHKCHANGE notification message which is sent to the parent window (usually
	a dialog). The notification can be handled by adding a notification handler as
	shown below using a parent dialog window as an example:
	
	  // header file
	  class CChecktestDlg : public CDialog
	  {
	  protected:
	  	afx_msg void OnSelchangeList1();
	  	afx_msg void OnChkChange();
	  ...
	  };
	
	  // cpp file
	  BEGIN_MESSAGE_MAP(CChecktestDlg, CDialog)
	      ON_LBN_SELCHANGE(IDC_LIST1, OnSelchangeList1)
	      ON_CONTROL(CLBN_CHKCHANGE, IDC_LIST1, OnChkChange)
	  END_MESSAGE_MAP()
	
	  void CChecktestDlg::OnSelchangeList1() 
	  {
	      TRACE("OnSelchangeList1 called\n");	
	  }
	
	  void CChecktestDlg::OnChkChange() 
	  {
	      TRACE("OnChkChange called\n");	
	  }
	
	The notification handler for LBN_SELCHANGE is also shown to demonstrate the
	difference between the two notifications. If the check state of an item is set,
	the item is also selected (clearing the check box does not cancel the item).
	However, changing the selection state does not affect the check state. Since
	there was no macro similar to ON_LBN_SELCHANGE, ON_CONTROL was used.
	
	The behavior of the CCheckListBox was modified between Visual C++ version 5.0 and
	Visual C++ version 6.0. MFC in Visual C++ version 6.0 added the following
	method:
	
	  void SetSelectionCheck(int nCheck)
	
	where nCheck has the same meaning in CCheckListBox::SetCheck:
	
	 0 - clear
	 1 - checked
	 2 - indeterminate
	
	SetSelectionCheck changes the check state of all selected items to the state of
	nCheck. When an item that is selected is checked in Visual C++ version 6.0,
	SetSelectionCheck changes the check state for all the other selected items. Keep
	this in mined when handling check notifications.
	
	REFERENCES
	==========
	
	Q194298 INFO: Changes Between MFC 4.22 and 6.0
	
	Additional query words: CCheckListBox, SetSelectionCheck, CLBN_CHKCHANGE
	
	======================================================================
	Keywords          : kbCtrl kbListBox kbMFC kbVC500 kbVC600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : :5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
