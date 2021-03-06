---
layout: page
title: "Q196833: EditGrid.exe: Edit Cells in MSFlexGrid ActiveX Control"
permalink: /kb/196/Q196833/
---

## Q196833: EditGrid.exe: Edit Cells in MSFlexGrid ActiveX Control

{% raw %}

	Article: Q196833
	Product(s): Microsoft C Compiler
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbfile kbole kbsample kbActiveX kbCOMt kbContainer kbCtrl kbMFC kbVC500 kbGrpDSMFCATL
	Last Modified: 03-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Flex Grid Control (MSFlexGrid), which ships with Visual C++ and
	Visual Basic, does not support editing of individual cells.
	
	The Visual Basic Programmer's Guide has an example that shows how to
	programmatically add this functionality by placing a TextBox control over the
	cell to be edited, and then updating the cell programmatically.
	
	EditGrid.exe is a sample that shows the steps needed to implement this feature in
	Microsoft Visual C++ using MFC.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  EditGrid.exe
	  (http://download.microsoft.com/download/vc50pro/Sample5/1/NT4/EN-US/EditGrid.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	
	NOTE: Use the -d option when running EditGrid.exe to decompress the file and
	recreate the proper directory structure.
	
	Steps to Add Editing Support to MSFlexGrid
	------------------------------------------
	
	1. Use the Component Gallery to add the MSFlexGrid to your project. This creates
	  MFC based wrapper classes for the control.
	
	2. Use ClassWizard to create a new generic CWnd-derived class named CEditGrid.
	  After you create this class, change it so it is derived from the MSFlexGrid
	  class. See the REFERENCES section of this article for more information.
	
	3. Use ClassWizard to create a new CEdit-derived class named CEditWnd. Handle
	  the WM_CHAR and WM_KEYDOWN messages:
	
	        void CEditWnd::OnChar(UINT nChar, UINT nRepCnt, UINT nFlags)
	        {
	           if (nChar != 13) // Ignore ENTER key.
	              CEdit::OnChar(nChar, nRepCnt, nFlags);
	        }
	
	        void CEditWnd::OnKeyDown(UINT nChar, UINT nRepCnt, UINT nFlags)
	        {
	           if (nChar == 27) // Esc means "Cancel".
	           {
	              SetWindowText("");
	              ShowWindow(SW_HIDE);
	              GetParent()->SetFocus();
	           }
	           else if (nChar == 13)  // Enter means "OK".
	              GetParent()->SetFocus();
	
	           CEdit::OnKeyDown(nChar, nRepCnt, nFlags);
	        }
	
	4. Add the following member variables to CEditGrid:
	
	        public:
	           CEditWnd m_edit;
	           long m_lBorderWidth;
	           long m_lBorderHeight;
	
	           int m_nLogX;
	           int m_nLogY;
	
	5. Override the PreSubclassWindow() virtual function for CEditGrid:
	
	        void CEditGrid::PreSubclassWindow()
	        {
	           // Calculate border size.
	           SetRow(0);
	           SetCol(0);
	           m_lBorderWidth = GetCellLeft();
	           m_lBorderHeigth = GetCellTop();
	
	           // To convert grid rect from twips to DC units you need
	           // pixels per inch.
	           CDC* pDC = GetDC();
	           m_nLogX = pDC->GetDeviceCaps(LOGPIXELSX);
	           m_nLogY = pDC->GetDeviceCaps(LOGPIXELSY);
	           ReleaseDC(pDC);
	
	           // Create invisible edit control.
	           m_edit.Create(WS_CHILD|ES_MULTILINE|ES_WANTRETURN,
	              CRect(0,0,0,0), this, GetDlgCtrlID());
	        }
	
	6. Handle the KeyPress, DBLClick, and LeaveCell reflected events in CEditGrid.
	  To do this, you need to add an event map to the class:
	
	     EditGrid.h
	
	        protected:
	           afx_msg void OnKeyPressGrid(short FAR* KeyAscii);
	           afx_msg void OnDblClickGrid();
	           afx_msg void OnUpdateGrid();
	           DECLARE_EVENTSINK_MAP()
	
	     EdtGrid.cpp
	
	        BEGIN_EVENTSINK_MAP(CEditGrid, CMSFlexGrid)
	        // {{AFX_EVENTSINK_MAP(CEditGrid)
	        // }}AFX_EVENTSINK_MAP
	           ON_EVENT_REFLECT(CEditGrid, -603 /* KeyPress */, OnKeyPressGrid,
	                            VTS_PI2)
	           ON_EVENT_REFLECT(CEditGrid, -601 /* DblClick */, OnDblClickGrid,
	                            VTS_NONE)
	           ON_EVENT_REFLECT(CEditGrid, 72 /* LeaveCell */, OnUpdateGrid,
	                            VTS_NONE)
	        END_EVENTSINK_MAP()
	
	        void CEditGrid::OnDblClickGrid()
	        {
	           short i = 13;
	           OnKeyPressGrid(&i); // Simulate a return.
	        }
	
	        void CEditGrid::OnKeyPressGrid(short FAR* KeyAscii)
	        {
	
	           ASSERT (KeyAscii != NULL);
	
	           m_edit.SetWindowText(GetText());
	
	           if (*KeyAscii == 13)
	              m_edit.SetSel(0,-1);
	           else
	           {
	              char buf[] = " ";
	              buf[0] = (char)*KeyAscii;
	              m_edit.SetSel(-1,-1);
	              m_edit.ReplaceSel(buf);
	           }
	
	           // Adjust for border height and convert from twips to screen
	           // units.
	           m_edit.MoveWindow(((GetCellLeft() - m_lBorderWidth) *
	                                               m_nLogX)/1440,
	              ((GetCellTop() - m_lBorderHeight) * m_nLogY)/1440,
	              (GetCellWidth()* m_nLogX)/1440,
	              (GetCellHeight()* m_nLogY)/1440, FALSE);
	
	           m_edit.ShowWindow(SW_SHOW);
	           m_edit.SetFocus();
	        }
	
	        void CEditGrid::OnUpdateGrid()
	        {
	           // Check to see if edit is visible.
	           BOOL bVisible = ::GetWindowLong(m_edit.GetSafeHwnd(), GWL_STYLE)
	                             & WS_VISIBLE;
	           if (bVisible)
	           {
	              CString cStr;
	              m_edit.GetWindowText(cStr);
	              SetText(cStr);
	              m_edit.SetWindowText("");
	              m_edit.ShowWindow(SW_HIDE);
	           }
	        }
	
	7. Handle the WM_GETDLGCODE and WM_SETFOCUS messages in CEditGrid:
	
	     UINT CEditGrid::OnGetDlgCode()
	     {
	        return DLGC_WANTALLKEYS;
	     }
	
	     void CEditGrid::OnSetFocus(CWnd* pOldWnd)
	     {
	        CMSFlexGrid::OnSetFocus(pOldWnd);
	
	        OnUpdateGrid();
	     }
	
	8. Create an instance of the CEditGrid control in either of the following ways:
	
	   - Add the MSFlexGrid control to a dialog box or CFormView using the Resource
	     Editor. You can then subclass the control by holding down the CTRL key and
	     double-clicking on the control in the Resource Editor. You must edit the
	     .h file, and change the class from CMSFlexGrid to CEditGrid.
	
	   - Create the control dynamically. To do this, you need to override the
	     CEditGrid::Create functions to call CMSFlexGrid::Create. You also need to
	     call CEditGrid::SubClassWindow() to subclass it. For more information, see
	     the REFERENCES section of this article.
	
	9. Set the following properties for the control:
	
	     Cols = 6
	     Rows = 20
	     FillStyle = 1 - Repeat
	     FocusRect = 2 - Heavy
	
	If you add the control to a dialog box or CFormView, you can use the Resource
	Editor. Otherwise, you need to do this programmatically after you create and
	subclass the control.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q99161 HOWTO: Derive From Classes not Listed in ClassWizard
	
	  Q156051 Messages Not Received by Dynamically Created Control
	
	  Q173026 PRB: Message-Handlers For ActiveX Control Aren't Called
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by Kelly Marie
	Ward, Microsoft Corporation
	(c) Microsoft Corporation 1998, All Rights Reserved.
	Contributions by Kelly Marie Ward, Microsoft Corporation
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbfile kbole kbsample kbActiveX kbCOMt kbContainer kbCtrl kbMFC kbVC500 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:5.0
	
	=============================================================================
	

{% endraw %}
