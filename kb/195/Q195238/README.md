---
layout: page
title: "Q195238: PRB: MFC Control Does Not Detect Keystrokes When SSTabs Exist"
permalink: /kb/195/Q195238/
---

## Q195238: PRB: MFC Control Does Not Detect Keystrokes When SSTabs Exist

{% raw %}

	Article: Q195238
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbcode kbActiveX kbCtrl kbVBp kbVBp600 kbVC kbGrpDSVB kbCodeSam kbMFC600
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An MFC-based ActiveX control cannot gain input focus when an SSTab control is on
	the same form. This only happens when you click the MFC control (at which time
	the MFC control should get the input focus) right after you have clicked one of
	the SSTab's tab pages. The control works as expected when there is no SSTab on
	the form or when you click the MFC control after clicking other controls, such
	as the Visual Basic intrinsic TextBox. As an example, if the MFC control
	aggregates a child Edit box control, and if you click it right after you've
	clicked the SSTab's tab page, nothing can be typed into your MFC control's Edit
	box.
	
	CAUSE
	=====
	
	MFC ActiveX controls UI-Activate themselves when they receive the mouse- click
	message. If you have a child control inside your COleControl, mouse- click
	messages on the child control are not sent to the COleControl and MFC does not
	UI-Activate the ActiveX control, even though the child control has just been
	given the keyboard focus. When the SSTab gets the focus, your control needs to
	explicitly UI-Activate itself to actually get the input focus when you click the
	control.
	
	RESOLUTION
	==========
	
	There are two ways to resolve the problem. The first method needs to change the
	MFC control's source code. The idea is to UI-Activate the whole control whenever
	your control is activated. Usually, this is done with an event handler, such as
	the following:
	
	     int CMyEditCtlAppCtrl::OnMouseActivate(CWnd* pDesktopWnd,
	               UINT nHitTest, UINT message)
	     {
	        OnActivateInPlace (TRUE, NULL); // UI-Activate the control
	        return COleControl::OnMouseActivate(pDesktopWnd, nHitTest, message);
	     }
	
	The second method changes the Visual Basic code. The only change that needs to be
	made is to call the SetFocus method of one of the controls on the form in the
	SSTab1_Click event handler. Then, after you click the SSTab control, other
	controls on the form can get the input focus.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Create an MFC ActiveX Control with an Edit Child Control
	-----------------------------------------------------------------
	
	1. Open Visual C++. Select New from the File menu. Create a new MFC ActiveX
	  control wizard project. Use MyEditCtlApp as the project's name and accept all
	  the default settings. Click "finish" to actually create the project.
	
	2. Add a contained Edit control object to the control by adding the following
	  lines to the MyEditCtlAppCtl class declaration in the MyEditCtlAppCtl.h
	  file:
	
	        private:
	           CEdit m_Edit;
	
	3. Add the following line to the MyEditCtlAppCtl class declaration in the
	  MyEditCtlAppCtl.h file to provide OnCreate message handling function:
	
	        afx_msg int OnCreate(LPCREATESTRUCT lpCreateStruct);
	
	4. Add the following line to the MessageMap (within BEGIN_MESSAGE_MAP and
	  END_MESSAGE_MAP pair) in MyEditCtlAppCtl.cpp file:
	
	        ON_WM_CREATE()
	
	5. Add the following lines to the MyEditCtlAppCtl.cpp file to implement the
	  OnCreate function:
	
	        int CMyEditCtlAppCtrl::OnCreate(LPCREATESTRUCT lpCreateStruct)
	        {
	           // Call the base class's OnCreate
	           if (COleControl::OnCreate(lpCreateStruct) == -1)
	             return -1;
	
	           // Create the edit control
	           CRect rClient;
	           CString strTemp = "";
	           GetClientRect(rClient);
	           m_Edit.Create(WS_CHILD | WS_VISIBLE | WS_VSCROLL | WS_OVERLAPPED |
	                  WS_CLIPSIBLINGS | ES_MULTILINE | ES_WANTRETURN,
	                  rClient, this, 123L);
	           m_Edit.SetWindowText(strTemp);
	           return 0;
	         }
	
	6. Build the project by pressing the F7 key or selecting "Build
	  MyEditCtlApp.ocx" from the Build menu and the control will be automatically
	  registered.
	
	Steps to Create a Visual Basic Test Project
	-------------------------------------------
	
	1. Open Visual Basic and create a Visual Basic standard EXE project. Form1 is
	  created by default.
	
	2. Choose "Components" from the Project menu to bring up the project components
	  dialog. Find "MyEditCtlApp ActiveX Control Module" in the list and select the
	  checkbox beside of it. Click on the "Apply" button and a new icon with "ocx"
	  will be added to the tool box. You may then close the components dialog.
	
	3. Add a MyEditCtlApp control to the form.
	
	4. Run the application. You can click the control and type in characters without
	  problem.
	
	5. Stop the application.
	
	6. Choose "Components" from the Project menu to bring up the project components
	  dialog. Find "Microsoft Tabbed Dialog Control 6.0" in the list and select the
	  checkbox beside of it. Click on the "Apply" button and an icon for the tab
	  control will be added to the tool box. You can then close the components
	  dialog.
	
	7. Put an SSTab control to the form and enlarge it so that it can hold other
	  controls.
	
	8. Put a MyEditCtlApp controls on SSTab tab0 and tab1.
	
	9. Run the application. Now, if you click the SSTab control's tab0, tab1, etc.,
	  and then click any MyEditCtlApp control, you cannot type in any characters.
	  This is the problem.
	
	Steps to Fix the Problem in C++
	-------------------------------
	
	1. Open the MyEditCtlApp project in Visual C++.
	
	2. Add the following line to the MyEditCtlAppCtl class declaration in the
	  MyEditCtlAppCtl.h file to overload the OnMouseActivate virtual function:
	
	        virtual int OnMouseActivate(CWnd* pDesktopWnd, UINT nHitTest, UINT);
	
	3. Add the following line to the MessageMap (within BEGIN_MESSAGE_MAP and
	  END_MESSAGE_MAP pair) in MyEditCtlAppCtl.cpp file:
	
	        ON_WM_MOUSEACTIVATE()
	
	4. Add the following lines to the MyEditCtlAppCtl.cpp file to implement the
	  OnMouseActivate function:
	
	        int CMyEditCtlAppCtrl::OnMouseActivate(CWnd* pDesktopWnd,
	                 UINT nHitTest, UINT message)
	        {
	           OnActivateInPlace (TRUE, NULL); //UI-Activate the control
	           return COleControl::OnMouseActivate(pDesktopWnd,
	                      nHitTest, message);
	        }
	
	5. Rebuild the project and run the Visual Basic test project. This time,
	  everything works as expected.
	
	Steps to Fix the Problem in Visual Basic
	----------------------------------------
	
	1. Open the Visual Basic test project with the old MFC control.
	
	2. Add the following code to the form's code window where MyEditCtlApp2 can be
	  replaced with any MyEditCtlApp control placed on Tab control:
	
	        Private Sub SSTab1_Click(PreviousTab As Integer)
	           MyEditCtlApp2.SetFocus
	        End Sub
	
	3. Run the application and note that everything works as expected.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbActiveX kbCtrl kbVBp kbVBp600 kbVC kbGrpDSVB kbCodeSam kbMFC600 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
