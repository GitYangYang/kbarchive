---
layout: page
title: "Q156684: How to Use NLTEST to Force a New Secure Channel"
permalink: /kb/156/Q156684/
---

## Q156684: How to Use NLTEST to Force a New Secure Channel

{% raw %}

	Article: Q156684
	Product(s): Microsoft Windows NT
	Version(s): WINNT:3.51 4.0
	Operating System(s): 
	Keyword(s): kbtool
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	To validate access to resources in a trusting domain, the trusting domain's
	primary domain controller (PDC) establishes a secure channel with a domain
	controller in the trusted domain. Pass-through authentication then occurs over
	this secure channel. However, in WAN environments, the trusted domain's domain
	controllers may be dispersed over a wide variety of fast and slow links. If a
	fast link is unavailable at the time when the trusting domain's PDC wants to
	establish a secure channel, the secure channel may be established with a domain
	controller over a slow link. Even when the fast link is reestablished,
	pass-through authentications may be sent over a slow link to the trusted
	domain's domain controller.
	
	
	You can use the NLTEST utility to break and re-initialize a secure channel.
	NLTEST is a Windows NT Server 4.0 Resource Kit utility that is used to get
	information about an existing trust or to reset a trust's secure channel.
	
	MORE INFORMATION
	================
	
	The mechanism for establishing a secure channel is very similar to a normal user
	logon process. That is, the trusting domain's domain controllers send out logon
	requests to all known domain controllers in the trusted domain. The trusting
	domain controllers then set up a secure channel with the first trusted domain
	controller that responds to this request.
	
	Normally, this method is preferred because the first domain controller to respond
	to a logon request is typically the controller that is located across the
	fastest communication link. However, if that link is down or the "fast" domain
	controller is unavailable, a domain controller over a slower link may respond
	first, and all pass-through authentications will be made over this slow link.
	
	Currently, no mechanism in Windows NT Server checks for a suitably fast
	connection. Also, in current versions of Windows NT Server, there is no way to
	select a preferred trusted domain controller to handle the secure channel.
	
	
	However, there is a mechanism in place to track how long it takes to do an
	authentication over the existing secure channel. If a pass-through
	authentication takes more than 45 seconds, that fact is noted. If two such
	authentications exceed that limit, a rediscovery process begins, the current
	secure channel is broken, and the trusting domain's PDC once again sends out
	logon requests to all known trusted domain controllers.
	
	However, because this mechanism tracks only communications that take longer than
	45 seconds, users may see a 40-second delay every time they attempt to use a
	resource without a secure-channel reset taking place.
	
	NLTEST is a command-line utility that you can use to check on secure channel
	status, as well as other information (such as when the secure channel password
	was last changed) useful in a trusting environment. You can also use NLTEST to
	restart the discovery process for a new trusted domain controller. The syntax of
	NLTEST is:
	
	NLTEST /sc_query:<Account Domain>
	
	Where <Account Domain> is the name of the trusted domain. This returns the
	name of the trusted domain controller with which the trusting PDC has a secure
	channel. If that domain controller is unacceptable, use the following syntax:
	
	NLTEST /sc_reset:<Account Domain>
	
	You should run NLTEST on the trusting domain's PDC.
	
	Along with running NLTEST manually, it is possible to write a small batch process
	that periodically (perhaps using the Windows NT Server AT Scheduler) runs the
	first query, compares the resulting controller's name against a list of
	acceptable controllers, and then uses the reset command if necessary. This does
	not guarantee that a "fast" domain controller will be located, but it gives
	users the current fastest connection available.
	
	Additional query words: passthrough passthru pass-thru thru
	======================================================================
	Keywords          : kbtool 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : WINNT:3.51 4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
