---
layout: page
title: "Q106690: Function for Returning a Julian Date in FoxPro"
permalink: /kb/106/Q106690/
---

## Q106690: Function for Returning a Julian Date in FoxPro

{% raw %}

	Article: Q106690
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:2.0,2.5,2.5a,2.5b; WINDOWS:2.5,2.5a,2.5b,3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 05-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5, 2.5a, 2.5b 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The FoxPro functions SYS(1) and SYS(11) return a Julian day number, which is
	different from a Julian date. To return a Julian date, you can write a
	user-defined function (UDF), as described below.
	
	MORE INFORMATION
	================
	
	SYS(1) and SYS(11) return a date according to the Julian calendar, in which each
	day is counted, with day 1 being in 4713 B.C. On the other hand, a Julian date
	is a date represented by a five-digit number, the first two digits being the
	last two digits of the year, and the final three digits being the number of days
	that have elapsed since January 1 of that year. For example, 01/01/93 according
	to the Julian calendar is 2448989, whereas the Julian date is 93001.
	
	The following program calls a UDF that converts a date in FoxPro date format to a
	Julian date.
	
	     * Begin program
	     @1,1 SAY "Enter a date" GET testdate DEFAULT {  /  /  }
	     READ
	     @2,1 SAY "The Julian Date of "+ DTOC(testdate) + " is " ;
	        + TRANSFORM(julian(testdate),'99999')
	     *End program
	
	     FUNCTION julian
	     PARAMETER tdate
	
	     *isolate the year and convert it to a string
	     cYear = RIGHT(DTOC(tdate),2)
	     firstjan = CTOD("01/01/" + cYear)
	
	     *calculate the sequential number of the day
	     jday = tdate-firstjan+1
	
	     *position the year at the two leftmost digits
	     nYear = VAL(cYear) * 1000
	
	     *combine year and day number
	     jdate = nYear + jday
	
	     RETURN jdate
	     *End Function julian
	
	Additional query words: VFoxWin FoxDos FoxWin format
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro250 kbFoxPro250a kbFoxPro250b kbVFP300
	Version           : MS-DOS:2.0,2.5,2.5a,2.5b; WINDOWS:2.5,2.5a,2.5b,3.0
	
	=============================================================================
	

{% endraw %}
