---
layout: page
title: "Q326444: HOW TO: Configure the URLScan Tool"
permalink: /kb/326/Q326444/
---

## Q326444: HOW TO: Configure the URLScan Tool

{% raw %}

	Article: Q326444
	Product(s): Internet Information Server
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): kbHOWTOmaster
	Last Modified: 09-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Install URLScan
	   - Modify the URLScan.ini file
	
	      - The [Options] Section
	      - The [AllowVerbs] and [DenyVerbs] Sections
	      - The [DenyHeaders] Section
	      - The [AllowExtensions] and [DenyExtensions] Sections
	      - The [DenyUrlSequences] Section
	
	   - Configure URLScan For Use With IIS-Dependent Applications
	
	- REFERENCES
	
	SUMMARY
	=======
	
	This step-by-step article explains how to configure the URLScan tool to protect
	your Web server from attacks and exploits.
	
	Install URLScan
	---------------
	
	For additional information about how to install URLScan, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q315522 HOW TO: Extract the URLScan Tool and Lockdown Template Files from the
	  IIS Lockdown Tool
	
	  Q307608 INFO: Availability of URLScan Version 2.5 Security Tool
	
	
	Modify the URLScan.ini File
	---------------------------
	
	All configuration of URLScan is performed through the URLScan.ini file, which is
	located in the %WINDIR%\System32\Inetsrv\URLscan folder. To configure URLScan,
	open this file in a text editor such as Notepad, make the appropriate changes,
	and then save the file. You must restart Internet Information Services (IIS) for
	your changes to take effect.
	
	The URLScan.ini file contains the following sections:
	
	- [Options]: This section describes general URLScan options.
	
	- [AllowVerbs] and [DenyVerbs]: This section defines the verbs (also known as
	  HTTP methods) that URLScan permits.
	
	- [DenyHeaders]: This section lists HTTP headers that are not permitted in an
	  HTTP request. If an HTTP request contains one of the HTTP headers that are
	  listed in this section, URLScan rejects the request.
	
	- [AllowExtensions] and [DenyExtensions]: This section defines the file name
	  extensions that URLScan permits.
	
	- [DenyURLSequences]: This section lists strings that are not permitted in an
	  HTTP request. URLScan rejects HTTP requests that contain a string that
	  appears in this section.
	
	Each section will be described in more detail in this document.
	
	The [Options] Section:
	
	In the [Options] section, you can configure a number of URLScan options. Each
	line in this section has the following format:
	
	  <OptionName>=<OptionValue>
	
	The available options and their default values are as follows:
	
	- UseAllowVerbs=1
	
	  By default, this option is set to 1. If this option is set to 1, URLScan only
	  permits HTTP requests that use the verbs that are listed in the [AllowVerbs]
	  section. URLScan blocks any requests that do not use these verbs. If this
	  option is set to 0, URLScan ignores the [AllowVerbs] section, and instead
	  blocks only requests that use verbs that are listed in the [DenyVerbs]
	  section.
	
	- UseAllowExtensions=0
	
	  By default, this option is set to 0. If this option is set to 0, URLScan
	  blocks requests for file name extensions that are listed in the
	  [DenyExtensions] section, but permits requests for any other file name
	  extensions. If this option is set to 1, URLScan only permits requests for
	  files with extensions that are listed in the [AllowExtensions] section, and
	  it blocks requests for any other files.
	
	- NormalizeUrlBeforeScan=1
	
	  IIS receives requests that are URL encoded. This means that certain characters
	  may be replaced with a percent sign (%) followed by a particular number. For
	  example, %20 corresponds to a space, so a request for
	  http://myserver/My%20Dir/My%20File.htm is the same as a request for
	  http://myserver/My Dir/My File.htm. Normalization is the process of decoding
	  URL-encoded requests. By default, this option is set to 1. If the
	  NormalizeUrlBeforeScan option is set to 1, URLScan analyzes the decoded
	  request. If it is set to 0, URLScan analyzes the undecoded request instead.
	  Setting this option to 0 hinders the ability of URLScan to block certain
	  kinds of attacks.
	
	- VerifyNormalization=1
	
	  Because the percent sign (%) itself can be URL encoded, an attacker can submit
	  a carefully crafted request to a server that is basically double-encoded. If
	  this occurs, IIS may accept a request that it would otherwise reject as not
	  valid. By default, this option is set to 1. If the VerifyNormalization option
	  is set to 1, URLScan normalizes the URL two times. If the URL after the first
	  normalization is different from the URL after the second normalization,
	  URLScan rejects the request. This prevents attacks that rely on
	  double-encoded requests.
	
	- AllowHighBitCharacters=0
	
	  By default, this option is set to 0. If this option is set to 0, URLScan
	  rejects any requests that contain non-ASCII characters. This can prevent
	  certain types of attacks, but it may also block out requests for certain
	  legitimate files, such as files with non-English names.
	
	- AllowDotInPath=0
	
	  By default, this option is set to 0. If this option is set to 0, URLScan
	  rejects any request that contains multiple periods (.). This prevents
	  attempts to disguise requests for dangerous file name extensions by putting a
	  safe file name extension in the path information or query string portion of
	  the URL. For example, if this option is set to 1, URLScan might permit a
	  request for http://servername/BadFile.exe/SafeFile.htm because it thinks that
	  it is a request for an HTML page, when it is actually a request for an
	  executable (.exe) file with the name of an HTML page in the PATH_INFO area.
	  When this option is set 0, URLScan may also deny requests for directories
	  that contain periods.
	
	- RemoveServerHeader=0
	
	  By default, a Web server returns a header that identifies what Web server
	  software it is running in all responses. This can increase the server
	  vulnerability because an attacker can determine that a server is running IIS
	  and then attack known IIS problems, instead of trying to attack an IIS server
	  by using exploits that are designed for other Web servers. By default, this
	  option is set to 0. If you set the RemoveServerHeader option to 1, you
	  prevent your server from sending the header that identifies it as an IIS
	  server. If you set RemoveServerHeader to 0, this header is still sent.
	
	- AlternateServerName=(not specified by default)
	
	  If RemoveServerHeader is set to 0, you can specify a string in the
	  AlternateServerName option to specify what will be passed back in the Server
	  header. If RemoveServerHeader is set to 1, this option is ignored.
	
	- EnableLogging=1
	
	  By default, URLScan keeps a complete log of all blocked requests in
	  %WINDIR%\System32\Inetsrv\URLScan. You can set EnableLogging to 0 if you do
	  not want to keep this log.
	
	- PerProcessLogging=0
	
	  By default, this option is set to 0. If this option is set to 1, URLScan
	  creates a separate log for each process that hosts URLScan.dll. If it is set
	  to 0, all processes log to the same file.
	
	- PerDayLogging=1
	
	  By default, this option is set to 1. If this value is set to 1, URLScan
	  creates a new log file each day. Each log file is named
	  Urlscan.<MMDDYY>.log, where <MMDDYY> is the date of the log file.
	  If this value is set to 0, all logging is saved in the same file, regardless
	  of the date.
	
	- AllowLateScanning=0
	
	  By default, this option is set to 0. If this option is set to 0, URLScan runs
	  as a high-priority filter, which means that it executes before any other
	  Internet Server Application Programming Interface (ISAPI) filters that are
	  installed on the server. If this option is set to 1, URLScan runs as a
	  low-priority filter, so that other filters can modify the URL before URLScan
	  performs any analysis. FrontPage Server Extensions (FPSE) requires this
	  option to be set to 1.
	
	- RejectResponseUrl=(not specified by default)
	
	  This option specifies the virtual path to a file that runs when URLScan blocks
	  a request. This permits you to customize the response that is sent to the
	  client for blocked requests. You must specify RejectResponseUrl as a virtual
	  path to the appropriate file, such as /Path/To/RejectResponseHandler.asp. You
	  can specify a file that URLScan typically blocks, such as an Active Server
	  Pages (ASP) page. You can also use the following server variables from the
	  page:
	
	   - HTTP_URLSCAN_STATUS_HEADER: This specifies why the request has been
	     blocked.
	
	   - HTTP_URLSCAN_ORIGINAL_VERB: This specifies the original verb from the
	     blocked request (for example, GET, POST, HEAD, or DEBUG).
	
	   - HTTP_URLSCAN_ORIGINAL_URL: This specifies the original URL from the
	     blocked request.
	
	If you set RejectResponseUrl to the special value of /~*, URLScan uses
	logging-only mode. This permits IIS to serve all requests, but it adds an entry
	to the URLScan log for any requests that are typically blocked. This is useful
	if you want to test your URLScan.ini file.
	
	If you do not specify a value for RejectResponseUrl, URLScan uses the default
	value of /<Rejected-By-UrlScan>.
	
	- UseFastPathReject=0
	
	  By default, this option is set to 0. If this option is set to 1, URLScan
	  ignores the RejectResponseUrl setting and immediately returns a 404 error
	  message to the browser. This is faster than processing RejectResponseUrl, but
	  it does not permit as many logging options. If this option is set to 0,
	  URLScan uses the RejectResponseUrl setting to process the request.
	
	The [AllowVerbs] and [DenyVerbs] Sections:
	
	The [AllowVerbs] and [DenyVerbs] sections define the HTTP verbs (also known as
	methods) that URLScan permits. Common HTTP verbs include GET, POST, HEAD, and
	PUT. Other applications, such as FPSE and Web Distributed Authoring and
	Versioning (WebDAV), use additional verbs.
	
	Both the [AllowVerbs] and the [DenyVerbs] sections have the same syntax. They are
	made up of a list of HTTP verbs, and each verb appears on its own line.
	
	URLScan decides which section to use based on the value of the UseAllowVerbs
	option in the [Options] section. By default, this option is set to 1. If
	UseAllowVerbs is set to 1, URLScan only permits requests that use the verbs that
	are listed in the [AllowVerbs] section. A request that does not use one of these
	verbs is rejected. In this case, the [DenyVerbs] section is ignored.
	
	If UseAllowVerbs is set to 0, URLScan denies requests that use verbs that are
	explicitly listed in the [DenyVerbs] section. Any requests that use verbs that
	do not appear in this section are permitted. In this case, URLScan ignores the
	[AllowVerbs] section.
	
	The [DenyHeaders] Section:
	
	When a client requests a page from a Web server, it typically sends over some
	HTTP headers that contain additional information about the request. Common HTTP
	headers include the following:
	
	- Host:
	
	  This header contains the name of the Web server.
	
	- Accept:
	
	  This header defines the file types that the client can handle.
	
	- User-Agent:
	
	  This header contains the name of the browser that requests the page.
	
	- Authorization:
	
	  This header defines the authentication methods that the client supports.
	
	Clients may send other headers to the server to specify additional information.
	
	In the [DenyHeaders] section, you define HTTP headers that URLScan will reject.
	If URLScan receives a request that contains any header that is listed in this
	section, it rejects the request. This section is made up of a list of HTTP
	headers, with each header appearing on its own line. Header names must be
	followed by a colon (:) (for example, Header-Name:).
	
	The [AllowExtensions] and [DenyExtensions] Sections:
	
	Most files have a file name extension that identifies what kind of file they are.
	For example, file names for Word documents typically end in .doc, HTML file
	names typically end in .htm or .html, and plain text file names typically end in
	.txt. The [AllowExtensions] and [DenyExtensions] sections permit you to define
	extensions that URLScan will block. For example, you can configure URLScan to
	reject requests for .exe files to prevent Web users from executing applications
	on your system.
	
	Both the [AllowExtensions] and the [DenyExtensions] sections have the same
	syntax. They are made up of a list of file name extensions, and each extension
	appears on its own line. The extension starts with a period (.) (for example,
	.ext).
	
	URLScan decides which section to use based on the value of UseAllowExtensions in
	the [Options] section. By default, this option is set to 0. If
	UseAllowExtensions is set to 0, URLScan only denies requests for file name
	extensions that are listed in the [DenyExtensions] section. Any file name
	extensions that are not listed in this section are permitted. The
	[AllowExtensions] section is ignored.
	
	If UseAllowExtensions is set to 1, URLScan denies requests for any file name
	extensions that are not explicitly listed in the [AllowExtensions] section. Only
	requests for a file name extension that is listed in that section are permitted.
	The [DenyExtensions] section is ignored.
	
	For additional information about how to configure URLScan to permit requests for
	files that do not have an extension, click the article number below to view the
	article in the Microsoft Knowledge Base:
	
	  Q312376 HOW TO: Configure URLScan to Allow Requests with a Null Extension in
	  IIS
	
	The [DenyUrlSequences] Section:
	
	You can configure URLScan to block requests that contain certain sequences of
	characters in the URL. For example, you can block requests that contain two
	consecutive periods (..), which are frequently used with exploits that take
	advantage of directory traversal vulnerabilities. To specify a character
	sequence to block, put the sequence on a line by itself in the
	[DenyUrlSequences] section.
	
	Note that adding character sequences may adversely affect Outlook Web Access
	(OWA) for Microsoft Exchange. When you open a message from OWA, the subject line
	of the message is contained in the URL that is requested from the server.
	Because the URLScan.ini file blocks any requests that contain the percent sign
	(%) and the ampersand sign (&), users receive a 404 error message when they
	try to open a message with a subject line such as "Sales increase by 100%" or
	"Bob & Sue are coming to town". To resolve this, you can remove these
	sequences from the [DenyUrlSequences] section. Note that this reduces security
	because it potentially permits damaging requests to reach the server.
	
	
	Configure URLScan For Use With IIS-Dependent Applications
	---------------------------------------------------------
	
	Applications such as Exchange, FPSE, and Microsoft Visual Studio .NET depend on
	IIS for correct functionality. If you do not configure URLScan correctly, these
	applications may stop working correctly.
	
	For additional information about how to configure URLScan to work with these
	applications, click the article numbers below to view the articles in the
	Microsoft Knowledge Base:
	
	  Q309508 XCCC: IIS Lockdown and URLscan Configurations in an Exchange
	  Environment
	
	  Q309394 HOW TO: Use URLScan with FrontPage 2000
	
	  Q318290 HOW TO: Use URLScan with FrontPage 2002
	
	  Q310588 PRB: Security Toolkit Breaks ASP.NET Debugging in Visual Studio .NET
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q325864 HOW TO: Install and Use the IIS Lockdown Wizard
	
	Additional query words: lockdown
	
	======================================================================
	Keywords          : kbHOWTOmaster 
	Technology        : kbiisSearch kbiis500 kbiis400
	Version           : :4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
