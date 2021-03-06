---
layout: page
title: "Q139308: How to Simulate a Spinner Control for Character Values"
permalink: /kb/139/Q139308/
---

## Q139308: How to Simulate a Spinner Control for Character Values

{% raw %}

	Article: Q139308
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 11-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The current Spinner control only displays numeric Values. This article shows by
	example how to simulate a character- or text-based Spinner control. The examples
	show continuous looping of the values to be displayed. As an example, when
	decrementing from the letter A, the letter Z is displayed rather than not
	allowing the Spinner value to move beyond what would normally be a stop point.
	
	MORE INFORMATION
	================
	
	Code Sample
	-----------
	
	  *Start of Program **************************
	
	  frmSpinners = CREATEOBJECT("frmTextSpinner")
	  frmSpinners.show
	  READ EVENTS
	
	  DEFINE CLASS frmTextSpinner AS Form
	
	       Top      = 42
	       Left     = 36
	       Height   = 90
	       Width    = 182
	       DoCreate = .T.
	       Caption  = "Text Spinners"
	       Name     = "Form1"
	
	       ADD OBJECT spnSpinner1 AS Spinner WITH ;
	            Alignment        = 1, ;
	            BackColor        = RGB(192,192,192), ;
	            ForeColor        = RGB(192,192,192), ;
	            Height           = 25, ;
	            Left             = 143, ;
	            Margin           = 0, ;
	            SpecialEffect    = 1, ;
	            SpinnerHighValue = 91.00, ;
	            SpinnerLowValue = 64.00, ;
	            Top             = 8, ;
	            Width           = 15, ;
	            Value           = 65.00, ;
	            Name            = "spnSpinner1"
	
	       ADD OBJECT txtText1 AS Textbox WITH ;
	            BorderStyle = 1, ;
	            Value       = "A", ;
	            Height      = 25, ;
	            Left        = 120, ;
	            Top         = 8, ;
	            Width       = 23, ;
	            Name        = "txtText1"
	
	       ADD OBJECT spnSpinner2 AS Spinner WITH ;
	            Alignment        = 1, ;
	            BackColor        = RGB(192,192,192), ;
	            ForeColor        = RGB(192,192,192), ;
	            Height           = 25, ;
	            Left             = 46, ;
	            Margin           = 0, ;
	            SpecialEffect    = 1, ;
	            SpinnerHighValue = 91.00, ;
	            SpinnerLowValue  = 64.00, ;
	            Top              = 8, ;
	            Width            = 15, ;
	            Value            = 65.00, ;
	            Name             = "spnSpinner2"
	
	       ADD OBJECT Label1 AS Label WITH ;
	            Alignment   = 2, ;
	            BorderStyle = 1, ;
	            Caption     = "A", ;
	            Height      = 25, ;
	            Left        = 24, ;
	            Top         = 8, ;
	            Width       = 23, ;
	            Name        = "Label1"
	
	       ADD OBJECT spnSpinner3 AS Spinner WITH ;
	            Alignment        = 1, ;
	            BackColor        = RGB(192,192,192), ;
	            ForeColor        = RGB(192,192,192), ;
	            Height           = 25, ;
	            Left             = 142, ;
	            Margin           = 0, ;
	            SpecialEffect    = 1, ;
	            SpinnerHighValue =   8.00, ;
	            SpinnerLowValue  =   0.00, ;
	            Top   = 49, ;
	            Width = 15, ;
	            Value = 1.0, ;
	            Name  = "spnSpinner3"
	
	       ADD OBJECT Label2 AS Label WITH ;
	            BorderStyle = 1, ;
	            Caption     = "Monday", ;
	            Height      = 25, ;
	            Left        = 23, ;
	            Top         = 49, ;
	            Width       = 120, ;
	            Name        = "Label2"
	
	       PROCEDURE spnSpinner1.InteractiveChange
	            DO CASE
	                 CASE This.Value=91
	                      This.Value=65 && Goes a "A" from "Z"
	                 CASE This.Value=64
	                      This.Value=90 && Goes a "Z" from "A"
	            ENDCASE
	
	            ThisForm.txtText1.Value=CHR(This.Value)
	            ThisForm.txtText1.SetFocus
	       ENDPROC
	
	       PROCEDURE spnSpinner2.InteractiveChange
	            DO CASE
	                 CASE This.Value=91
	                      This.Value=65 && Goes a "A" from "Z"
	                 CASE This.Value=64
	                      This.Value=90 && Goes a "Z" from "A"
	            ENDCASE
	
	            ThisForm.Label1.Caption=CHR(This.Value)
	       ENDPROC
	
	       PROCEDURE spnSpinner3.InteractiveChange
	            IF This.Value=8
	                 This.Value=1 && Goes from "Sunday" to "Monday"
	            ENDIF
	            IF This.Value=0
	                 This.Value=7 && Goes from "Monday" to "Sunday"
	            ENDIF
	
	            DO CASE
	            CASE This.Value = 1
	                 ThisForm.Label2.Caption="Monday"
	            CASE This.Value = 2
	                 ThisForm.Label2.Caption="Tuesday"
	            CASE This.Value = 3
	                 ThisForm.Label2.Caption="Wednesday"
	            CASE This.Value = 4
	                 ThisForm.Label2.Caption="Thursday"
	            CASE This.Value = 5
	                 ThisForm.Label2.Caption="Friday"
	            CASE This.Value = 6
	                 ThisForm.Label2.Caption="Saturday"
	            CASE This.Value = 7
	                 ThisForm.Label2.Caption="Sunday"
	            ENDCASE
	       ENDPROC
	  ENDDEFINE
	  *End of Program **************************************
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
