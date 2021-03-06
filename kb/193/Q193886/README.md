---
layout: page
title: "Q193886: How to Index Physical Roots"
permalink: /kb/193/Q193886/
---

## Q193886: How to Index Physical Roots

{% raw %}

	Article: Q193886
	Product(s): Internet Information Server
	Version(s): 2.0,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-FEB-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Index Server version 2.0 
	- Microsoft Internet Information Server 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Using Microsoft Index Server 2.0, you can index physical paths and virtual
	paths. This allows you to index data and return UNC pathing or FTP URLs to
	access the data.
	
	MORE INFORMATION
	================
	
	You must first add the physical folders to the catalog. To do this, perform the
	following steps:
	
	1. Expand the tree for the catalog in the Microsoft Management Console (MMC) by
	  right-clicking the Directories folder.
	
	2. Choose New and then choose Directory.
	
	3. In the dialog box, include the full path to the directory that you want to
	  index, along with the alias that you want returned in the search. Normally,
	  the alias is \\machine\directory to point to a share where these files are
	  located, or FTP://machine/directory to point to an FTP location of the data.
	
	4. For Type, choose Include to include the directory in the catalog. Note:
	  Exclude removes the catalog from the index (which is useful for excluding a
	  subdirectory of a directory that you have included.)
	
	When you have added the physical paths to the catalog, you then need to create a
	search page to retrieve the results. Normally, searches are run in the virtual
	namespace by setting the scope of the query to "/.". Setting the scope to "\"
	will perform the search against all documents in the physical namespace. In your
	search page, set the scope to "\." In an .idq file, set the scope to CiScope=\.
	If you use the IXSSO object in a .asp file, the scope will be set similar to the
	following:
	
	  util.AddScopeToQuery Q, "\", "deep"
	
	  -or-
	
	  FormScope=\ (if you are using the samples).
	
	The results of this query will not have a vpath record, but will have a path
	record that contains the local path to the data on this computer. However, the
	path needs to be returned using the alias you entered in step 3. Add the path
	column to the CiColumn statement in the .idq file, or to the Q.Columns statement
	in the .asp file. You will not get the alias as a result, because the catalog
	you are querying is on the same computer as Index Server. By default, Index
	server will display the local pathing in this case, not the alias.
	
	To return the path using the alias created in step 3, point to the catalog using
	Named Pipes. The statement in an .idq file is as follows:
	
	  CiCatalog=query://<machine>/<catalog>
	
	In an .asp file using the IXSSO object, the statement is as follows:
	
	  Q.Catalog = "query://<machine>/<catalog>"
	
	In both examples above, <machine> is the name of the server hosting the
	catalog, and <catalog> is the name of the catalog as it appears in the
	Index Server snap-in for the MMC.
	
	The final step is to modify the results page of the query so that it returns the
	local path, not the vpath.
	
	One drawback of this method is that authentication is limited to Anonymous or
	Basic authentication. Windows NT Challenge Response will not work with this
	Named Pipe query. This is a limitation of current Windows NT security.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbIdxServSearch kbAudDeveloper kbiis400 kbIdxServ200
	Version           : :2.0,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
