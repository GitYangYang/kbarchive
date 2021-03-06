---
layout: page
title: "Q154675: FP: How to Edit/Delete Articles in a FrontPage Discussion Web"
permalink: /kb/154/Q154675/
---

## Q154675: FP: How to Edit/Delete Articles in a FrontPage Discussion Web

{% raw %}

	Article: Q154675
	Product(s): Word Front Page
	Version(s): 1.0,1.1
	Operating System(s): 
	Keyword(s): kbusage kbdta
	Last Modified: 02-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows with Bonus Pack 
	- Microsoft FrontPage for Windows, versions 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 2000/2002 version of this article, see Q196126.
	
	For a Microsoft FrontPage 98 version of this article, see Q194106.
	
	SUMMARY
	=======
	
	This article describes how to edit or delete an article (page) submitted to a
	FrontPage discussion Web in FrontPage Explorer.
	
	MORE INFORMATION
	================
	
	To delete or edit an article in a FrontPage discussion Web, use the appropriate
	method for your version of FrontPage.
	
	FrontPage 97 and 1.1
	--------------------
	
	1. In FrontPage Explorer, open the Web.
	
	2. On the Tools menu, click Web Settings, and then click the Advanced tab.
	
	3. Under Options, click to select the "Show documents in hidden directories"
	  check box.
	
	4. Click Apply, click Yes, and then click OK.
	
	5. On the View menu, click Folder. Expand the Discussion Web Table Of Contents.
	
	6. Select the article you want to edit or delete.
	
	  The links to the individual articles are represented as links from the
	  Tocproto.htm page. The address (URL) of each discussion group article ends
	  with an eight-digit integer (these addresses are created in sequential
	  order).
	
	   - To edit the article, open it and make the changes you want.
	
	   - To delete the article, open it and delete all the text in the article, or
	     replace it with a message like Content Removed by Moderator.
	
	     NOTE: Do not delete the article. Doing so can result in orphaned discussion
	     articles.
	
	7. Save the file without changing the URL.
	
	8. On the Tools Menu, click Recalculate Hyperlinks.
	
	9. On the View menu, click Refresh.
	
	FrontPage 1.0 for Windows
	-------------------------
	
	NOTE: In FrontPage 1.0, if you delete a page in the middle of a threaded
	FrontPage Web, the "previous" and "next" links on the navigation bar break.
	Therefore, Microsoft recommends that you edit the page rather than delete the
	page. In FrontPage versions 1.1 and later, "previous" and "next" links are
	unaffected when you delete articles from the middle of the thread.
	
	1. Open the Web in FrontPage Explorer.
	
	2. On the Tools menu, click Web Settings, and then click the Parameters tab.
	
	3. Click Add, and then type "vti_showhiddenpages" (without the quotation marks).
	  Leave the Value field blank. Click OK.
	
	4. Refresh the FrontPage Web by clicking Refresh on the View menu.
	
	5. On the View menu, click Folder. Locate the Tocproto.htm page.
	
	6. On the View menu, click Outline to see the links from the Tocproto.htm file.
	
	7. Find the article that you want to edit or delete.
	
	  The address (URL) of each discussion group article ends with an eight-digit
	  integer (these addresses are created in sequential order).
	
	   - To edit the article, open it in FrontPage Editor and make the changes you
	     want. Save the file without changing the URL.
	
	     NOTE: DO NOT open the Tocproto.htm file in a program OTHER than FrontPage
	     Editor. Doing so will break links to that file.
	
	   - To delete the article, open it in FrontPage Editor and delete all the text
	     in the article, or replace it with a message like Content Removed by
	     Moderator.
	
	     NOTE: Do not delete the article. Doing so can result in orphaned discussion
	     articles.
	
	8. Save the file without changing the URL.
	
	Additional query words: 97 post posting postings front page
	
	======================================================================
	Keywords          : kbusage kbdta 
	Technology        : kbFrontPageSearch kbFrontPage1xSearch kbFrontPage97Search kbZNotKeyword3 kbFrontPage100 kbFrontPage110
	Version           : :1.0,1.1
	Hardware          : x86
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
