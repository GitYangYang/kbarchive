---
layout: page
title: "Q66578: Program Crashes If Run on a Machine Without an 80x87"
permalink: /kb/066/Q66578/
---

## Q66578: Program Crashes If Run on a Machine Without an 80x87

{% raw %}

	Article: Q66578
	Product(s): See article
	Version(s): 6.00
	Operating System(s): OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 9-NOV-1990
	
	Question:
	
	I have a multithreaded application that I developed on a system with
	an 80x87 coprocessor. Everything is working properly; however, when I
	try to run the code on a machine that doesn't have a coprocessor, it
	always fails with a General Protection fault. I have tried all
	variations of the run-time library (LLIBCMT.LIB and CDLLOBJS.LIB) to
	no avail. Is there a problem with using the multithreaded run-time
	libraries on a machine without a coprocessor?
	
	Response:
	
	There is no problem with using the multithreaded run-time libraries on
	a machine without a coprocessor.
	
	The problem is probably caused by not using _beginthread() to start
	the threads that perform the floating point calculations. If you use
	DosCreateThread() to start the thread, there is required
	initialization code that is not performed in the run-time for that
	thread; this is mandatory because 80x87 emulation is performed in the
	run-time in cases where there is no coprocessor.

{% endraw %}
