---
layout: page
title: "Q61970: CodeView 3.00 Fades with Monochrome VGA"
permalink: /kb/061/Q61970/
---

## Q61970: CodeView 3.00 Fades with Monochrome VGA

{% raw %}

	Article: Q61970
	Product(s): See article
	Version(s): 3.00   | 3.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 11-JUL-1990
	
	If you invoke CodeView version 3.00 on certain machines with
	monochrome VGA monitors and then trace through several lines of code,
	the screen will fade and become unreadable. Exiting and re-entering
	CodeView refreshes the screen, but the screen immediately starts to
	fade again.
	
	This problem is caused by an error in the video ROM BIOS and has been
	verified to occur on the following machines:
	
	l. PS/2 Model P70 with monochrome VGA
	
	2. Siemens with Video 7 monochrome VGA
	
	3. Northgate 386 with Video 16 monochrome VGA
	
	The following are different methods of working around this problem:
	
	1. Switch into color mode using the mode CO80 command (may not have
	   any effect).
	
	2. From the options menu inside Codeview, turn flip/swap off using
	   the screen-swap option.
	
	   If you don't want to give up flip/swap functionality, try option 3.
	
	3. If the video BIOS is replaceable, replace it with an updated video
	   BIOS.
	
	4. If the video BIOS is not replaceable, replace the card.

{% endraw %}
