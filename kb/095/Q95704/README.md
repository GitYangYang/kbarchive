---
layout: page
title: "Q95704: PRB: ? Command Drops Carriage Return/Linefeed"
permalink: /kb/095/Q95704/
---

## Q95704: PRB: ? Command Drops Carriage Return/Linefeed

{% raw %}

	Article: Q95704
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:2.0,2.5,2.5a; WINDOWS:2.5,2.5a,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5, 2.5a 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are using the question mark (?) command to send information to the
	printer, occasionally a carriage return and linefeed (CR/LF) combination is
	dropped and information is printed on the same line. For example, you may
	receive the following printed output:
	
	  customer_name customer_lastname
	  customer_name customer_lastname customer_name customer_lastname
	  customer_name customer_lastname
	
	RESOLUTION
	==========
	
	Use the ?? command in place of the ? command. Because the ?? command does not
	send a carriage return and linefeed automatically, you must send them manually
	by adding CHR(13)+CHR(10) to the end of each line. The following example shows
	the correct use of the ?? command:
	
	     SET PRINTER to LPT1
	     SET PRINTER ON
	     SELECT customer
	   
	     SCAN ALL WHILE !EOF()
	       ?? customer.contact+" "+customer.company+CHR(13)+CHR(10)
	     ENDSCAN
	     SET PRINTER TO
	
	Additional query words: VFoxWin FoxDos FoxWin format break line feed
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250 kbFoxPro250a kbVFP300
	Version           : MS-DOS:2.0,2.5,2.5a; WINDOWS:2.5,2.5a,3.0
	
	=============================================================================
	

{% endraw %}
