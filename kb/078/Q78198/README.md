---
layout: page
title: "Q78198: Move'Em Memory Manager from Qualitas"
permalink: /kb/078/Q78198/
---

## Q78198: Move'Em Memory Manager from Qualitas

{% raw %}

	Article: Q78198
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:3.x,4.x,5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Qualitas Inc. Move'Em is a program loader designed to load device drivers and
	memory resident programs into the upper memory area (UMA). Qualitas states that
	Move'Em is fully compatible with MS-DOS versions 3.0 and later.
	
	Move 'Em is not a memory manager. This utility can backfill conventional memory
	with existing expanded memory, but does not manage (or provide) extended or XMS
	memory.
	
	MORE INFORMATION
	================
	
	Move'Em facilitates the moving of device drivers, network system drivers, and
	memory resident programs out of the first 640K of conventional memory. These
	drivers and programs are moved into the upper memory blocks (UMB) in the memory
	range from 640K to 1 MB. Move'Em provides a resident program optimization
	utility for automatically determining the most efficient loading order.
	
	In systems with less than 640K system memory, Move'Em backfills the conventional
	memory with expanded memory to provide a full 640K of usable system memory. This
	feature requires an EMS 4.0 compatible memory board or specific chip sets. This
	feature does not support XMS memory management.
	
	System Requirements:
	
	- Microsoft MS-DOS or IBM PC-DOS version 3.0 or later
	
	- Either an 80286 or 80386 based IBM PC compatible computer with a NEAT, LEAP,
	  or AT\386 CHIPSet from Chips & Technologies with at least 1 MB of memory
	
	-or-
	
	- An IBM PC compatible computer with a fully hardware compatible EMS 4.0 board
	  with at least 256K of expanded memory
	
	REFERENCES
	==========
	
	Qualitas technical support: (301) 907-7400
	
	  Qualitas, Inc. 7101 Wisconsin Avenue Suite 1386 Bethesda, MD 20814
	
	Additional query words: 3.x 4.x 5.00 3rdparty noupd
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401
	Version           : MS-DOS:3.x,4.x,5.0
	
	=============================================================================
	

{% endraw %}
