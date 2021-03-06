---
layout: page
title: "Q180141: XADM: Recurring Address Book Views in Exchange Server"
permalink: /kb/180/Q180141/
---

## Q180141: XADM: Recurring Address Book Views in Exchange Server

{% raw %}

	Article: Q180141
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 28-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	Microsoft Exchange Server has the ability to order and group recipient objects
	(mailboxes, custom recipients, DLs) into Address Book Views (ABVs), based on
	various object properties that these recipient objects may have in common, for
	example, Company Name, Country, State, Custom attribute, and so on.
	
	Once the ABV is defined, objects meeting the criteria will be automatically added
	to the view; a "child-view" is auto-created if this is the first object with
	these Group by Attribute (GBA) property specifics. This is performed by a
	periodic background task (every 5 minutes, typically) known as View Consistency
	Checker (VCC).
	
	For example, suppose an ABV called By Country is defined that includes recipient
	objects (Mailbox, CR, and so on) grouped by whatever is specified in the Country
	field (a GBA) (under Properties on the General tab). The first recipient defined
	with Ireland specified in the country field will result in a child-view titled
	Ireland being automatically created under the ABV root object, By Country.
	
	This auto-create functionality (VCC), combined with some obvious and not-so-
	obvious recipient object properties or conditions, can result in the unexpected
	behavior of, or persistent, ABVs.
	
	MORE INFORMATION
	================
	
	ABVs are unique Directory objects. An ABV GBA defined in one site becomes a
	global GBA and can be modified in sites throughout the organization. In
	contrast, recipient objects that have a property matching a GBA, and thus
	populating a view, can originate in any site. However, these recipient objects
	remain modifiable (writeable replicas) only from within their originating site.
	
	Proper planning and careful implementation of ABVs can help you maintain accurate
	and useful views. In particular, ensuring proper spelling within the fields used
	for generating ABVs, and astute awareness of "hidden recipients" (template
	mailboxes or otherwise) should be practiced. Additionally, maintaining timely
	directory replication throughout the organization is essential for successful
	ABV management.
	
	Deleting
	--------
	
	Empty subcontainers and ABVs (root level) whose subcontainers are empty can be
	deleted.
	
	Hidden recipients are not detected by the Delete process, so containers that have
	only hidden recipients will be deleted, temporarily. When VCC next runs, the
	hidden recipients will be detected, and the ABV\subcontainer re-created. If
	empty ABVs mysteriously re-appear, check for hidden recipients in the
	re-appearing container (on the View menu, click Hidden Recipients in Exchange
	Server Administrator program and view the contents of the container). Empty ABVs
	could also result from orphaned objects (see below).
	
	ABV Deletion Latency
	--------------------
	
	If the recipient object responsible for regenerating the view is from another
	site, the appropriate changes must be made to that object within its home site,
	and this change must replicate throughout the organization, so that VCC (in any
	other site) will no longer "rediscover" the object and regenerate the view.
	
	Furthermore, in the case of permanently removing a view from the org, it is
	essential that all changes required to remove all objects under the view be
	completed and allowed to replicate fully throughout the organization before
	actually deleting the view. Unless all objects capable of causing the view to be
	regenerated are removed (or modified) from the entire organization before you
	delete the view, the view can re-appear. This is an architectural compromise in
	ABV design, because VCC automatically generates ABVs but does not automatically
	delete empty ABVs. Without this compromise, ABVs would be functionally less
	effective.
	
	
	General recommendations:
	
	- Carefully plan and administer ABVs.
	
	- Administer ABV centrally, particularly in larger organizations. Due to the
	  ABV deletion latency mentioned above, if multiple administrators are
	  modifying the same ABVs at various sites simultaneously, it will be
	  increasingly difficult to provide consistent views across the organization.
	  (This is similar to the replication conflict that can occur within a site if
	  the same object is modified on two different servers at the same time.)
	
	
	- If the organization is very large, and\or replication latency throughout
	  organization is unknown, and an ABV needs to be deleted, consider the
	  following procedure:
	
	  1. Identify all objects currently populating the view, and modify or delete
	     them in their origin sites as appropriate so they will no longer populate
	     the view.
	
	  2. [From the "Central Administration site\server"] preface the "Display Name"
	     of the ABV with "zzz", so that it will appear at the end of the list.
	
	  3. [From the "Central Administration site\server"] If this is a root-level
	     ABV, disable its appearance in the Address Book by clearing the "<view
	     properties>, Advanced page, Show this view in client address book"
	     checkbox.
	
	  4. Wait a reasonable number days of before actually deleting the ABV from the
	     "Central Administration site\server". By default, tombstone lifetimes are
	     30 days, so waiting the full tombstone lifetime from when the recipient
	     objects were modified (step "a" above) is recommended.
	
	NOTE: Modifying a site's tombstone lifetime is not advised, as it will not hasten
	replication nor otherwise improve replication latency - furthermore, it could
	result in orphaned objects (which is undesirable - see below).
	
	Orphaned Recipient Objects Causing Re-Appearance of Deleted ABVs
	----------------------------------------------------------------
	
	An orphaned recipient object can result in the persistent re-appearance of an
	empty ABV if that orphan object includes GBA properties that would result in the
	auto-creation of the ABV.
	
	Consider the example above in the SUMMARY section of this article. In this case,
	an orphaned mailbox with a misspelled country name of "Irland" would result in
	an ABV under "By Country" of "Irland" being generated with this mailbox under
	it.
	
	Of course, the orphaned object only exists within one (or more) sites, but not
	it's original site. Thus, the ABV created in the orphan site will replicate to
	all the other sites, but, since the other sites don't maintain a replica of the
	orphan object, they replicate in the view, but cannot populate it with any
	object.
	
	Since there is no object under the child-view, the view can be deleted (in the
	sites that don't have the orphan) using Exchange Admin, <parent-ABV>,
	Properties, Advanced tab, Remove Empty Containers. This delete replicates
	throughout the organization, but once the site with the orphan attempts to
	delete the view, either: a) it fails to delete the view because it isn't empty;
	or b) in the case of the orphan also being a hidden object - after the view's
	deletion, the VCC will later execute, re-discover the orphan and it's qualifying
	GBA, determine that the child-view "Irland" doesn't exist, and recreate the
	child-view. Either way, the child-view will again replicate elsewhere.
	
	Resolution for Recurring, Unwanted ABVs
	---------------------------------------
	
	An ABV recurs because an object somewhere in the organization is being
	re-discovered by VCC. This object could be a valid object (possibly hidden), or
	an orphan object (possibly hidden).
	
	Valid objects should be visible in Admin (viewing hidden recipients requires
	selecting "View, Hidden recipients" in Admin). Valid objects should be modified
	appropriately in their originating site, and once the modification replicates
	throughout the organization, the previous ABV can be deleted (review the
	"General recommendations" above).
	
	Removing undesired recurring ABVs due to orphan objects requires that the orphan
	object be remedied first, and then the clean-up of the ABV can proceed as
	documented above. This can be complicated by the fact that the view may appear
	in every site, but only the site harboring the orphan will "populate" the view
	with a causal object (also, remember that the orphan object could be hidden).
	
	Finding the Site Harboring the Orphan
	-------------------------------------
	
	The ABV may contain recipient objects. If the ABV contains objects, then the
	originating site of these objects is revealed by viewing the recipient object's
	"DSA-Signature" raw property, and determining which site\server this object came
	from by comparing this DSA-Signature to a list of "Invocation-Ids" for the
	organization.
	
	
	If the ABV is empty, and the possibility of a hidden object has been dismissed,
	tracing the origin of the view occurs in the following sequence:
	
	1. View this ABV's DSA-Signature.
	
	2. Match this DSA-Signature to a server in the list of Invocation-IDs.
	
	3. Examine the ABV for orphans on the directory matching the DSA-Signature
	  listed in step 2 by running Admin.exe against that Exchange Server computer.
	
	4. Repeat steps 1, 2, and 3 until the ABV with the orphan object site\server is
	  located (don't forget to look for hidden objects).
	
	Obviously, this procedure may require examining objects in directories of various
	sites. Cooperation and coordination between Exchange Server site administrators
	may be required.
	
	Resolving the orphan object:
	
	Once the orphan's location has been determined the orphan's raw properties should
	be examined to determine the true origin site of the orphan, and the orphan
	object should be resolved using one of the options documented in the Knowledge
	Base article referenced below.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q179573 XADM: Orphaned Objects and Exchange Server Directory
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : WinNT:5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
