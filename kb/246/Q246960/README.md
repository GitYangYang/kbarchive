---
layout: page
title: "Q246960: HOWTO: Force Graphics to Always Download to Client"
permalink: /kb/246/Q246960/
---

## Q246960: HOWTO: Force Graphics to Always Download to Client

{% raw %}

	Article: Q246960
	Product(s): Internet Information Server
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbVisID600 kbDSupport kbIIS kbiis400
	Last Modified: 11-MAY-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Web sites that change graphic images frequently but utilize the same names for
	those images face a potential problem because browsers may cache the images and
	not rerequest them when they display the page.
	
	A scenario that is becoming more common is a site that generates real-time
	reports every few minutes and saves each report as an image. If browsers cache
	the image, the updated reports may not be displayed.
	
	This article describes two recommended solutions and one that is generally not
	recommended.
	
	MORE INFORMATION
	================
	
	Use one of the following two methods to make sure that graphic files expire so
	that they are not cached by browsers:
	
	- Use Internet Information Server's "Custom HTTP Headers" feature to add
	  standard headers that tell the browser to either "expire" or to not cache the
	  images. This technique works best when all the images are stored on the
	  server's hard disk in a few folders. Configure the folders so that the
	  desired headers are applied to all content served out of those folders.
	
	  To do so, open the Internet Services Manager and navigate to the folder that
	  contains the images. In the Properties dialog box for the folder, select HTTP
	  Headers, and then click Add. Type a header name, such as "cache-control"
	  (without the quotation marks) and its value, such as "no-cache" (without the
	  quotation marks).
	
	  Headers required to ensure that graphics are not cached include:
	
	  cache-control:no-cache
	  pragma:no-cache
	  expires:0
	
	- With applications for which image files do not have a centralized location,
	  you can write an Internet Server API (ISAPI) filter that examines the mime
	  type of the outgoing responses and applies a specific set of HTTP headers to
	  certain packets.
	
	  For additional information regarding ISAPI, search http://msdn.microsoft.com
	  for "ISAPI" or visit the support site
	  http://support.microsoft.com/support/isapi.
	
	Note that if the browser already has a cached copy of a particular graphic when
	the headers are implemented, it may be necessary to empty the browser's cache
	before the browser will consistently rerequest a given image. To empty the cache
	in Internet Explorer 5 or later, from the Tools menu, select Internet Options,
	and then click Delete Files.
	
	Not Recommended Due to Performance Lag
	--------------------------------------
	
	There is one technique that was commonly used in the past that is no longer
	preferred because it degrades performance. This method is to set HTTP headers on
	graphic images to have the client image tag reference an Active Server Pages
	(ASP) page as such:
	
	  <img src=graphicserver.asp?id=234>
	
	In this technique, the ASP page then uses the ID to read a specific image from
	the hard drive or database and uses Response.AddHeader and Response.BinaryWrite
	to stream the appropriate bits to the client with the desired HTTP headers.
	
	This technique does offer some advantages, such as the ability to manipulate the
	binary stream on the fly. But if your goal is merely to add HTTP headers, avoid
	it because of the performance loss.
	
	Additional query words: no-cache
	
	======================================================================
	Keywords          : kbVisID600 kbDSupport kbIIS kbiis400 
	Technology        : kbiisSearch kbiis400
	Version           : winnt:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
