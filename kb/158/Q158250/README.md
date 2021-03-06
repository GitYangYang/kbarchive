---
layout: page
title: "Q158250: FIX: Inherited Code Fires Twice with DODEFAULT()"
permalink: /kb/158/Q158250/
---

## Q158250: FIX: Inherited Code Fires Twice with DODEFAULT()

{% raw %}

	Article: Q158250
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0
	Operating System(s): 
	Keyword(s): kbprogramming kbvfp kbvfp500aFIXkbbuglist kbfixlist
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the DODEFAULT() function is used in a subclass method, it executes a method
	in the parent with the same name. When the parent has no method with that name,
	it then looks to the grandparent for that method. If it exists, it is executed.
	If the grandparent has a NODEFAULT() function, the code gets executed twice.
	
	CAUSE
	=====
	
	The parent in the above situation executes the code of the grandparent as its
	own. Because the grandparent has a NODEFAULT() function, the parent calls the
	method of the grandparent again.
	
	WORKAROUND
	==========
	
	To work around this problem, place a method that has the same name in the
	parent. Place a DODEFAULT() command in the parent method.
	
	STATUS
	======
	
	This behavior is by design in the products listed at the beginning of this
	article. This behavior does not occur in Visual FoxPro 5.0a
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a program with the following code:
	
	        ACTIVATE SCREEN
	        CLEAR
	        CREATEOBJECT("Test3")
	        RETURN
	
	        DEFINE CLASS Test AS Form
	        ENDDEFINE
	
	        DEFINE CLASS test1 AS Test
	           PROCEDURE Load
	              ACTIVATE SCREEN
	              ? "Class Test1, this.Class="+this.Class+ ;
	                ", this.ParentClass="+this.ParentClass
	                 DODEFAULT()
	           ENDPROC
	        ENDDEFINE
	
	        DEFINE CLASS test2 AS test1
	        ENDDEFINE
	
	        DEFINE CLASS test3 AS test2
	           PROCEDURE Load
	              ACTIVATE SCREEN
	              ? "Class Test3, this.Class="+this.Class+ ;
	                ", this.ParentClass="+this.ParentClass
	              DODEFAULT()
	           ENDPROC
	        ENDDEFINE
	
	2. Run the code. The Load method of test1 prints twice.
	
	Change Class test2 in the following way if you wish the code in test1 to execute
	only once:
	
	        DEFINE CLASS test2 AS test1
	          PROCEDURE Load
	             DODEFAULT()
	          ENDPROC
	        ENDDEFINE
	
	The above code prevents Class test2 from running class test1's code as its own.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbprogramming kbvfp kbvfp500aFIX kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500
	Version           : WINDOWS:5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
