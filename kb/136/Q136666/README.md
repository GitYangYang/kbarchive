---
layout: page
title: "Q136666: How to Make a Day Date Spinner"
permalink: /kb/136/Q136666/
---

## Q136666: How to Make a Day Date Spinner

{% raw %}

	Article: Q136666
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The "Using Spinners" section in chapter 11 of the Visual FoxPro Developer's
	Guide gives the following incorrect information:
	
	  If you want a user to be able to spin through a range of dates, you could
	  size the spinner so that only the buttons are visible and position a text box
	  beside the spinner buttons.
	
	It is not possible to size a spinner so that only the buttons are visible. The
	example in this article shows how to make a Day Date spinner and make it appear
	to be a single control.
	
	MORE INFORMATION
	================
	
	1. Create a new class called DayDateSpin based on Container.
	
	2. Store it in MyLib.vcx.
	
	3. Set the following properties for the DayDateSpin container:
	
	  BackStyle = 0 - Transparent
	  BorderWidth = 0
	  Height = 24
	  Width = 164
	
	4. Add a text box to the container, and set these properties:
	
	  FontName = Courier New   && Or any nonproportional font
	  FontSize = 9
	  Format = k    && Highlights the text box when the focus gets set to it.
	  Height = 22
	  Left = 0
	  ReadOnly = .T. && Keeps the user from editing the text box
	  Top = 1
	  Width = 148
	
	5. In the Init event procedure of the text box, add this code:
	
	     THIS.Value = PADR(CDOW(DATE()),11) + DTOC(DATE())
	     ** This puts current day and date in the text box when the form starts
	
	6. Add a spinner to the container and set these properties:
	
	  FontSize = 1
	  Height = 24
	  Left = 146
	  Top = 0
	  Width = 18
	
	7. On the Format menu, click Send to Back
	
	8. Add the following code to the spinner's DownClick event procedure:
	
	     dMyDate = CTOD(RIGHT(ALLTRIM(THIS.PARENT.Text1.Value),8))
	     ** Gets the Date from the text box
	     dMyDate = dMyDate - 1  && Decrease the date by one
	     THIS.PARENT.Text1.Value = PADR(CDOW(dMyDate),11) + DTOC(dMyDate)
	     **Stores the new day of the week and date back into the text box
	     THIS.PARENT.Text1.SetFocus
	
	9. Add the following code to the spinner's UpClick event procedure:
	
	     dMyDate = CTOD(RIGHT(ALLTRIM(THIS.PARENT.Text1.Value),8))
	     ** Gets the Date from the text box
	     dMyDate = dMyDate + 1  && Increment the date by one
	     THIS.PARENT.Text1.Value = PADR(CDOW(dMyDate),11) + DTOC(dMyDate)
	     **Stores the new day of the week and date back into the text box
	     THIS.PARENT.Text1.SetFocus
	
	10. Save and close the class.
	
	11. Create a new form. Then click the View Classes Icon on the Form Controls
	  toolbar. Click Add, and select MyLib.vcx.
	
	12. Pick the DayDateSpin class from the Form Controls toolbar, and place it on
	  the form.
	
	13. Save and run the form. Click the up arrow or down arrow to see the day and
	  date go up or down.
	
	REFERENCES
	==========
	
	For more infromation about creating classes and working with Visual FoxPro
	controls, please see chapters 10 and 11 in the Developer's Guide.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
