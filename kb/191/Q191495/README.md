---
layout: page
title: "Q191495: BUG: VC++ Tools with Long File Name (LFN) Parameters Fail on NT"
permalink: /kb/191/Q191495/
---

## Q191495: BUG: VC++ Tools with Long File Name (LFN) Parameters Fail on NT

{% raw %}

	Article: Q191495
	Product(s): Microsoft C Compiler
	Version(s): 2000,3.5,3.51,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kberrmsg kbide kbOSWin2000 kbVC500bug kbVC600bug kbGrpDSTools
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0, used with:
	   - the operating system: Microsoft Windows NT 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0, used with:
	   - the operating system: Microsoft Windows NT 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0, used with:
	   - the operating system: Microsoft Windows NT 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows 2000 Professional 
	- Microsoft Windows 2000 Server 
	- Microsoft Windows 2000 Advanced Server 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	
	On Windows NT and Windows 2000, running a batch file tool from the Visual C++
	Tools menu produces the following error message:
	
	  The name specified is not recognized as an internal or external command,
	  operable program or batch file
	
	On the Tools menu, click Customize. Select the Tools tab on the Customize dialog
	box. Note that the arguments contain one or more parameters surrounded with
	quote (") characters.
	
	This problem did not occur prior to installing a service pack for Visual Studio
	97.
	
	CAUSE
	=====
	
	Visual Studio 97 Service Pack 1 modified the method used to launch tools.
	Because Microsoft Windows 95, Microsoft Windows 98, Microsoft Windows Millennium
	Edition (Me), Windows NT, and Windows 2000 support long file names (LFNs) that
	can contain spaces, the tool launcher now automatically adds quotes around Tool
	commands. If the tool command is a batch file, it then launches the command
	processor--Cmd.exe on Windows NT--with the quoted command and any arguments:
	
	  CMD.EXE /c "<command>" <arguments>
	
	If a tool parameter might contain an LFN, you must place quotes around the
	argument: for example, "$(FileName)$(FileExt)". The resulting command launched
	from Visual C++ would look something like this:
	
	  CMD.EXE /c "mytool.cmd" "my LFN parameter"
	
	The parameter parsing logic in CMD.EXE strips the first quote and the last,
	preserving those in the interior. It then attempts to load the following:
	
	  mytool.cmd"
	
	That file name does not exist.
	
	RESOLUTION
	==========
	
	Following are some possible workarounds:
	
	- Use Cmd.exe as the command. In the argument field, type /C, the batch file
	  name, and the arguments:
	
	  Command: CMD.EXE
	  Arguments: /C mytool.bat "my LFN parameter"
	
	  If the tool resides in an LFN path with a space, place quotes around it and
	  also around the entire parameter string after the /C:
	
	  Arguments: /C ""my LFN path\mytool.bat" "my LFN parameter""
	
	- Do not put quotes in the tool's Arguments field.
	
	- Use an .exe file as the tool command rather than a batch file. The executable
	  could launch an appropriate batch file with the arguments properly
	  formatted.
	
	  NOTE: Visual Studio 6.0 solves the typical case by placing quotes around tools
	  that have a space in their path. However, a problem can still occur if the
	  tool meets this condition and also has quotes around any argument.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	
	MORE INFORMATION
	================
	
	
	If Cmd.exe has a /C or /K switch, it processes the remaining command line after
	the switch as a command. The following logic is used to process quote (")
	characters:
	
	If all of the following conditions are met, then quote characters on the command
	line are kept:
	
	- No /S switch
	
	- Exactly two quote characters
	
	- No special characters between the two quote characters, where special is one
	  of: &<>()@^|
	
	- One or more whitespace characters between the two quote characters
	
	- String between the two quote characters is the name of an executable file
	
	Otherwise, if the first character is a quote, strip it and remove the last quote
	character on the command line as well. Any text after the last quote character
	is kept.
	
	Steps to Reproduce Behavior
	---------------------------
	
	Use the following steps on a Windows NT workstation or server:
	
	1. Create a simple batch file, Badquote.bat, containing one line:
	
	        echo %1
	
	2. Open a CMD window that has Badquote.bat in its path. Here, C:\ is assumed for
	  the path. Type the following commands to verify its operation:
	
	  C:>badquote "hello, world"
	  Output: "hello, world"
	
	  C:>"badquote" "hello, world"
	  Output: "hello, world"
	
	  C:>CMD /c badquote "hello, world"
	  Output: "hello, world"
	
	3. At the command prompt, type the following:
	
	  C:>CMD /c "badquote" "hello, world"
	  Output: The name specified is not recognized as an internal or external
	  command, operable program or batch file.
	  Note the problem with CMD's parameter parsing.
	
	  C:>CMD /c ""badquote" "hello, world""
	  Output: "hello, world"
	  Note the workaround for proper parameter parsing.
	
	4. From the Tools menu, click Customize and Tool. Create an entry named "Test
	  LFNs":
	
	  Command: badquote
	  Arguments: "$(FileName)"
	  Don't forget the quotes. Keep 'Close window on exiting' unchecked.
	
	5. Open a file. Make it the active window.
	
	6. Click Tools, Test LFNs. The output will be as in step 3 above.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbide kbOSWin2000 kbVC500bug kbVC600bug kbGrpDSTools 
	Technology        : kbVCsearch kbAudDeveloper kbVC32bitSearch
	Version           : :2000,3.5,3.51,4.0,5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
