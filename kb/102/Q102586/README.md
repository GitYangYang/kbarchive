---
layout: page
title: "Q102586: PRB: Unable to Find Proc./Func. &lt;Name&gt;"
permalink: /kb/102/Q102586/
---

## Q102586: PRB: Unable to Find Proc./Func. &lt;Name&gt;

{% raw %}

	Article: Q102586
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:2.0,2.5,2.5a; WINDOWS:2.5,2.5a,3.0
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 05-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5, 2.5a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are building an application (.APP) from a project that makes reference
	to a function or procedure that is contained within another application, FoxPro
	is unable to resolve the external reference. The Build function will display the
	following error message:
	
	  Unable to Find Proc./Func. <name>
	
	RESOLUTION
	==========
	
	At the bottom of the file, create a procedure stub that references the external
	function.
	
	Additional ways to resolve this problem and their advantages and disadvantages
	are explained at the end of the "More Information" section below.
	
	NOTE: Using the EXTERNAL PROCEDURE <name> compiler directive does not
	resolve the problem.
	
	MORE INFORMATION
	================
	
	The code example below demonstrates this error. Because the main .APP file makes
	reference to a procedure stored in another .APP file, the Build function is
	unable to resolve the reference.
	
	1. Open a new program file. Name it SUBAPP.PRG and include the following code:
	
	        PROCEDURE MyFunc
	        WAIT WINDOW 'Myfunc called.'
	
	2. Save the program, and include it in a new project named SUBAPP.PJX. Save the
	  project, and build an application named SUBAPP.APP.
	
	3. Create a file named MAINAPP.PRG. Include the following code:
	
	        EXTERN PROCEDURE MyFunc
	        DO MyFunc IN SubApp.app
	
	4. Save the program and add it to a new project named MAINAPP.PJX. Save the
	  project and build an application named MAINAPP.APP.
	
	  During the build, as FoxPro is attempting to resolve external references, an
	  alert will appear with the following text:
	
	  Unable to Find Proc./Func. MYFUNC
	  Locate, Ignore, Ignore All, Cancel
	
	5. In the alert box, choose Locate and choose SUBAPP.APP, which contains the
	  procedure MyFunc. FoxPro will add the application as an excluded application
	  to the project MainApp and complete the build. Run MAINAPP.APP, and the wait
	  window will appear with the text "MyFunc called."
	
	6. Rebuild MAINAPP.PJX. Note that once again the "Unable to Find Proc./Func."
	  alert appears. Attempting to locate SUBAPP.APP again will add yet another
	  copy of the application as an excluded application to the project. You can
	  choose Ignore instead, and FoxPro will rebuild MAINAPP.APP without error.
	
	You can resolve this problem in one of three ways:
	
	- Choose Ignore when the Locate alert appears every time you rebuild your
	  project.
	
	-or-
	
	- Remove the reference to SUBAPP.APP from the MAINAPP project, pack the
	  project, and add a reference to the source program, in this case SUBAPP.PRG,
	  which contains the source code for the procedure MyFunc.
	
	-or-
	
	- Add the following code to the end of MAINAPP.PRG:
	
	        PROCEDURE MyFunc
	
	  This is a procedure stub that helps FoxPro resolve the external reference.
	  Since the line of code that actually calls the procedure explicitly specifies
	  the file in which the procedure actually resides, it is that procedure (in
	  this case, the procedure in SUBAPP.APP) which will be called.
	
	Notes
	-----
	
	Both the second and the third options will eliminate the problem. However, while
	the second option requires the source code to be available and that it be built
	into the application, increasing its size, the third option requires that the
	entire called application that includes the single function be sent along with
	the calling application. If the source code to the function is not available,
	and you would like to avoid the alert box, use the third method.
	
	Additional query words: VFoxWin FoxDos FoxWin errmsg err msg gengraph.app refreshgrph showgrph updategrph updategr genpd.app
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250 kbFoxPro250a kbVFP300
	Version           : MS-DOS:2.0,2.5,2.5a; WINDOWS:2.5,2.5a,3.0
	
	=============================================================================
	

{% endraw %}
