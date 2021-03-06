---
layout: page
title: "Q281940: BUG: DBCombo SelectedItem Property Is Not Updated When You Type"
permalink: /kb/281/Q281940/
---

## Q281940: BUG: DBCombo SelectedItem Property Is Not Updated When You Type

{% raw %}

	Article: Q281940
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbCtrl kbVBp kbVBp600bug kbGrpDSVB kbDSupport kbCodeSnippet
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the type-ahead searching features of the DBCombo control from
	DBList32.ocx, the SelectedItem property is not updated, and DBCombo does not
	reflect the matching entry that is found.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Visual Studio service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	NOTE: You must have a Visual Studio license agreement to obtain this fix.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	When you select an item in the list portion of a DBCombo control, the
	SelectedItem property contains a bookmark that you can use to reposition the
	selected record in the Recordset of the Data control that the RowSource property
	specifies. This property should be updated whether the user uses a mouse or the
	keyboard to select the item. Thus, when you use the type-ahead searching feature
	of this control, you expect that the SelectedItem property is updated after you
	type a name that matches a name in the list and press the ENTER key. In
	addition, the text in DBCombo should reflect the matching entry that is found.
	However, this functionality does not work when you use the standard Databound
	Combo and the Intrinsic Data control that shipped with Visual Basic 6.0.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create new Standard EXE project. Form1 is created by default.
	
	2. From the Project menu, click Components, select the "Data Bound List Controls
	  6.0" check box, and then click OK.
	
	3. Add a Databound combo, DBCombo1, to Form1.
	
	4. Add two TextBox controls, Text1 and Text2.
	
	5. Add a Data control, Data1.
	
	6. Configure the property settings of these controls as follows:
	
	  Data1 - Data control
	  DatabaseName = Biblio.mdb
	  RowSource = Authors
	  ReadOnly = True
	
	  Text2 - TextBox control
	  DataSource = Data1
	  DataField = Author
	  Visible = False
	
	  DBCombo1 - Databound Combo control
	  RowSource = Data1
	  ListField = Author
	
	7. Add the following code to the General Declarations section of Form1:
	
	  Option Explicit
	
	  Private Const UP_ARROW = 38
	  Private Const DOWN_ARROW = 40
	      
	  Private Sub Data1_Reposition()
	     '
	     ' Copy Text from Bound Text2 to Unbound Text1.
	     Text1.Text = Text2.Text
	  End Sub
	      
	  Private Sub DBCombo1_KeyUp(KeyCode As Integer, Shift As Integer)
	     Dim bmk As Variant
	     Dim x As Integer
	     Dim msg As String
	
	     On Error GoTo ErrHandler
	     '
	     ' Save Bookmark on CR and Arrow Key Activity.
	     Select Case KeyCode
	        Case Asc(vbCr), UP_ARROW, DOWN_ARROW
	            msg = "DBCombo1.SelectedItem has the value "
	            bmk = DBCombo1.SelectedItem
	            ' The next line raises error 13 if bmk has no value.
	            For x = 0 To UBound(bmk)
	                msg = msg & bmk(x)
	            Next x
	            Data1.Recordset.Bookmark = bmk
	            Debug.Print msg
	     End Select
	     Exit Sub
	              
	  ErrHandler:
	     If Err.Number = 13 Then   ' Type mismatch
	        Debug.Print "DBCombo1.SelectedItem is not assigned a value."
	     Else
	        MsgBox "Error " & Err.Number & ": " & Err.Description, vbCritical _
	           + vbOKOnly
	     End If
	  End Sub
	
	  Private Sub Form_Load()
	     Text1.Text = ""
	     DBCombo1.Text = ""
	  End Sub
	
	8. Run the project, and type a name that matches an entry in the bound DBCombo
	  control (such as "Curry, Dave" (without the quotation marks)).
	
	9. Press ENTER. Notice that the DBCombo1.SelectedItem property is not updated.
	
	10. Clear the text in DBCombo, and type a name that matches an entry in the list
	  (such as "Wellin, Paul" (without the quotation marks)).
	
	11. Press the UP ARROW or DOWN ARROW key. Notice that DBCombo1.SelectedItem is
	  updated with the bookmark for "Wellin, Paul".
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCtrl kbVBp kbVBp600bug kbGrpDSVB kbDSupport kbCodeSnippet 
	Component         : Component
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : :6.0
	Issue type        : kbbug kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
