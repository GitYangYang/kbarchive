---
layout: page
title: "Q313202: SSO Fails If Attach Does Not Contain LUWID or Other Subfield"
permalink: /kb/313/Q313202/
---

## Q313202: SSO Fails If Attach Does Not Contain LUWID or Other Subfield

{% raw %}

	Article: Q313202
	Product(s): Microsoft SNA Server
	Version(s): 4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Operating System(s): 
	Keyword(s): kbDSupport sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 kbhis2000 kbhis2000bug kbsna400sp4
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Advanced Program-to-Program Communications (APPC) or Common Programming
	Interface for Communications (CPI-C) applications that are configured to use the
	Single Sign-On (SSO) feature may fail to connect to a host system if the FMH-5
	(function management header) Attach message does not contain one or more of the
	following subfields:
	
	- Logical Unit of Work Identifier (LUWID) subfield
	
	- Conversation Correlator field
	
	- Password subfield (a subfield in the Access Security Information subfield,
	  which also ordinarily includes a User ID subfield)
	
	CAUSE
	=====
	
	The SNA Server service (Snaservr.exe) fails to correctly parse short FMH-5
	Attach messages. The FMH-5 Attach messages are short because they lack one or
	more subfields.
	
	RESOLUTION
	==========
	
	SNA Server 4.0
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft SNA Server version 4.0 service pack that contains this
	fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	+---------------------------------------------+
	| File name    | Date             | Time      | 
	+---------------------------------------------+
	| Snaservr.exe | 07-December-2001 | 7:50 A.M. | 
	+---------------------------------------------+
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	Host Integration Server 2000
	
	No fix is available for this problem in Host Integration Server 2000 at this
	time.
	
	STATUS
	======
	
	SNA Server 4.0
	
	Microsoft has confirmed this to be a problem in SNA Server versions 4.0, 4.0
	Service Pack (SP) 1, 4.0 SP2, 4.0 SP3, and 4.0 SP4.
	
	Host Integration Server 2000
	
	Microsoft has confirmed this to be a problem in Host Integration Server 2000.
	
	MORE INFORMATION
	================
	
	The following are configuration settings that result in an FMH-5 Attach message
	that does not include one or more of the necessary fields:
	
	- If the APPC or CPI-C application is running on an SNA Server 4.0 client or
	  SNA Server 4.0 system that is configured with registry entry "LUWIDSUP=NO",
	  the APPC dynamic link library (DLL) will not ask the SNA Server service to
	  generate an LUWID. The resulting FMH-5 Attach message will not include the
	  Logical Unit of Work Identifier subfield.
	
	- If an APPC or CPI-C application is designed to use a security type of AP_SAME
	  or CM_SECURITY_SAME, the FMH-5 Attach message may not include the password
	  subfield as part of the Access Security Information subfield.
	
	For more information on these and other fields and parameters that are included
	in FMH-5 Attach messages, see "FM Headers" in the IBM SNA Formats guide
	(GA27-3136).
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDSupport sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 kbhis2000 kbhis2000bug kbsna400sp4 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ400SP4
	Version           : :4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
