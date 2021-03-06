---
layout: page
title: "Q194948: HOWTO: Create a Child Console Process from a CGI Process"
permalink: /kb/194/Q194948/
---

## Q194948: HOWTO: Create a Child Console Process from a CGI Process

{% raw %}

	Article: Q194948
	Product(s): Internet Information Server
	Version(s): WINNT:3.0,4.0
	Operating System(s): 
	Keyword(s): kbCGI kbInternet kbWebServer
	Last Modified: 06-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 3.0, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When using the C-runtime routine _popen() to create a child process from within
	a CGI process, there are several issues regarding the mapping of STDIN and
	STDOUT (also STDERR) handles. By default Internet Information Server (IIS) 3.0
	and 4.0 will not create a console when a CGI process is created. The STDIN and
	STDOUT of the CGI process and that of the child process (created from the CGI
	process) will not be mapped correctly.
	
	MORE INFORMATION
	================
	
	When you have code such as below:
	
	     /* Parent.c -- This is the CGI process created by IIS */ 
	
	     int main(int argc, char *argv[])
	     {
	        FILE  *pFile = _popen("c:\\inetput\\scripts\\child.exe", "rt");
	        char  cBuf[256];
	
	        printf("HTTP/1.0 200 Ok\r\nContent-Type: test/html\r\n\r\n");
	        printf("<H1>I'm the Parent...</H1>");
	
	        while(!feof(pFile))
	        {
	           fgets(cBuf, 256, pFile);
	           printf("%s", cBuf);
	        }
	        _pclose (pFile);
	        return 0;
	     }
	
	     /* Child.c -- This is the child process created by Parent */ 
	
	     int main(int argc, char *argv[])
	     {
	        printf("<H1>Hello, I'm the child.</H1>");
	        return 0;
	     }
	
	The browser will not receive the message from the child process. This is because
	at the time that _popen() is called, the parent process does not have a console.
	Therefore, the STDIN, STDOUT, and STDERR are invalid (or more precisely are
	pseudo standard handles provided to the parent process by IIS). Therefore, the
	FILE pointer is created with STDIN/STDOUT, which do not map the child process.
	
	There are two ways to work around this default behavior.
	
	- Force IIS to launch all CGI application with their own console. Under IIS 3.0
	  this is done through the CreateProcessWithNewConsole DWORD registry entry
	  under HKLM\CurrentControlSet\Services\W3SVC\Parameters to 1. Under IIS 4.0,
	  this is done by setting the MD_CREATE_PROC_NEW_CONSOLE entry in the metabase
	  with IIS Admin Base Objects or corresponding CreateCGIWithNewConsole property
	  with IIS Admin Objects to TRUE (see IIS 4.0 online documentation).
	
	- If altering the configuration of IIS is not an option, you can
	  programmatically guarantee that the parent process will have a console by
	  issuing the AllocConsole() call. This call will fail if the parent already
	  has a console. But if the console does not exist, it will allocate one and
	  attach the parent process to this console. NOTE: AllocConsole() call must be
	  issued before the _popen() call is made; Otherwise, the resulting allocated
	  console's standard I/O handles will not have been picked up by the _popen()
	  routine.
	
	REFERENCES
	==========
	
	IIS 3.0 Product Documentation
	
	IIS 4.0 On Line Documentation
	
	======================================================================
	Keywords          : kbCGI kbInternet kbWebServer 
	Technology        : kbiisSearch kbiis400 kbiis300
	Version           : WINNT:3.0,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
