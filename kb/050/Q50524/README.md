---
layout: page
title: "Q50524: C Run-Time Routines Cannot Be Placed in an Overlay"
permalink: /kb/050/Q50524/
---

## Q50524: C Run-Time Routines Cannot Be Placed in an Overlay

{% raw %}

	Article: Q50524
	Product(s): See article
	Version(s): 5.10
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | S_QuickC S_QuickASM | mspl13_c
	Last Modified: 30-NOV-1989
	
	Problem:
	
	I want to extract a routine from the C Run-Time Library and put it in
	an overlay. The program compiles and links without warnings or errors,
	but when I run the program, my machine hangs.
	
	Response:
	
	The run-time routines for medium and large models (the only ones that
	overlays deal with) are compiled with /NT _TEXT. This puts all the
	routines in the same named segment. The linker cannot split a segment
	between the root and overlay. Segmentation takes precedence over
	overlays. The linker constructs overlays from segments, not individual
	functions.
	
	The first request for the segment (in an .OBJ that goes in root or in
	an overlay) determines where the linker will place the entire segment
	(root or overlay). If your extracted .OBJ is in the overlay, all the
	run time gets put into the overlay.
	
	Consequently, the entry point of the overlay manager is put into the
	overlay and not in the root, so the overlay manager code (also in
	_TEXT) is not present in memory at start up. This causes the machine
	to hang.

{% endraw %}
