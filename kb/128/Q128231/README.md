---
layout: page
title: "Q128231: WIN 3.1x: VIDC Entries in SYSTEM.INI and Descriptions"
permalink: /kb/128/Q128231/
---

## Q128231: WIN 3.1x: VIDC Entries in SYSTEM.INI and Descriptions

{% raw %}

	Article: Q128231
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1.0,1.0a,2.0
	Operating System(s): 
	Keyword(s): win31
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Ancient Lands for Windows, version 1.0 
	- Microsoft Art Gallery for Windows, version 1.0 
	- Microsoft Asimov for Windows 
	- Microsoft Dangerous Creatures for Windows, version 1.0 
	- Microsoft Dinosaurs for Windows, version 1.0 
	- Microsoft Encarta 96 Encyclopedia for Windows 
	- Microsoft Encarta 97 Encyclopedia for Windows 
	- Microsoft Encarta Encyclopedia 97 Deluxe for Windows 
	- Microsoft Office Professional Edition for Windows 
	- Microsoft Multimedia Schubert for Windows, version 1.0 
	- Microsoft Multimedia Strauss for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Solar System for Windows, version 1.0 
	- Microsoft Wine Guide for Windows, versions 1.0, 1.0a, 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following table lists drivers that have the "VIDC" prefix when they are
	listed in the [DRIVERS] section of the SYSTEM.INI file. The information reflects
	settings from an installation of the Intel INDEO R3.2 V3.22.01.43 and Video for
	Windows 1.1a releases.
	
	SYSTEM.INI
	[DRIVERS]
	Entry        Filename    Installed by    Description
	------------------------------------------------------------------------
	
	VIDC.CVID    ICCVID.DRV  -Ancient Lands   CINEPAK codec
	=ICCVID.DRV             -Bookshelf 1994
	                        -Cinemania 1995  Developed by SuperMac, and
	                        -Complete        licensed to Microsoft. It is a
	                         Baseball Guide  common off-line video codec used
	                        -Complete        with CD-ROM titles on both
	                         Basketball      Macintosh and Windows platforms.
	                        -Dangerous       It provides good video quality
	                         Creatures       and playback performance [320-by-
	                        -Dinosaurs       240 pixel at 30 frames per
	                        -Encarta 94-97   second (fps)]. It is known as an
	                        -MS Office       asymmetric codec. A codec that
	                         Professional    takes more time to compress than
	                         and Bookshelf   to decompress.
	                        -Asimov
	                        -Wine Guide
	                        -Scholastic's
	                         Magic School
	                         Bus Explores
	                         the Solar
	                         System
	
	VIDC.RT21    INDEOV.DRV  -Ancient Lands   INTEL'S INDEO(TM) VIDEO R2.1
	=INDEOV.DRV             -Cinemania 95
	                        -Complete        Older version of the Intel Indeo
	                         Baseball Guide  driver. See R3.2 below for
	                        -Complete        details.
	                         Basketball
	                        -Dangerous       (Used for backwards
	                         Creatures       compatibility.)
	                        -Encarta 95-97
	                        -MS Office
	                         Professional
	                         and Bookshelf
	                        -Asimov
	                        -Scholastic's
	                         Magic School
	                         Bus Explores
	                         the Solar
	                         System
	
	VIDC.RT31    INDEOV.DRV  -Ancient Lands   INTEL'S INDEO(TM) VIDEO DRIVER
	=INDEOV.DRV             -Cinemania 95
	                        -Complete        Older version of Intel's Indeo
	                         Basketball      video driver. See R3.2 below
	                        -Dangerous       for more details. (Used for
	                        -Creatures       backwards compatibility.)
	                        -Encarta 95-97
	                        -MS Office
	                         Professional
	                         and Bookshelf
	                        -Asimov
	                        -Scholastic's
	                         Magic School
	                         Bus Explores
	                         the Solar
	                         System
	
	VIDC.IV32    IR32.DLL    -Ancient Lands   INTEL INDEO(TM) VIDEO R3.2
	=IR32.DLL               -Cinemania 1995
	                        -Complete        This is the latest release of
	                         Basketball      Intel's video drivers. It
	                        -Dangerous       provides good quality video
	                         Creatures       playback (320-by-240 pixels at
	                        -Encarta 95-97   up to 30 fps with 8-bit mono
	                        -MS Office       audio) on any 486 without
	                         Professional    additional hardware. Using a
	                         and Bookshelf   powerful and complex algorithm,
	                        -Asimov          capable of executing many
	                        -Wine Guide      different modes of compression,
	                        -Scholastic's    this driver practically achieves
	                         Magic School    real-time performance.
	                         Bus Explores
	                         the Solar       This codec uses fixed palette
	                         System          color control that is located
	                        -World of Flight inside the indeo driver, not the
	                                         AVI file. It uses a 1:1
	                                         audio/video interleave thus
	                                         called an AVI file that
	                                         compresses the video file into a
	                                         24-bit per pixel format. Upon
	                                         decompression of this file, it
	                                         is converted into the 9-bit per
	                                         pixel format and played by the
	                                         YVU9.DRV (INTEL RAW Driver)
	                                         file.
	
	VIDC.YVU9    INDEOV.DRV -Ancient Lands    INTEL'S INDEO(TM) VIDEO RAW
	=INDEOV.DRV            -Cinemania 95
	                       -Complete         This Indeo driver converts each
	                        Basketball       video frame into a 9-bit per
	                       -Dangerous        pixel YUV color space and is
	                        Creatures        used uncompressed. It is  a
	                       -Encarta 95-97    color encoded scheme used for
	                       -MS Office        natural pictures in which the
	                        Professional     luminance and chrominance are
	                        and Bookshelf    separated. The basic building
	                       -Asimov           block  of the Indeo Video is a
	                       -Scholastic's     square of 4-by-4 block of 16
	                        Magic School     pixels. The brightness
	                        Bus Explores     information "Y", 16 bytes is all
	                        the Solar        kept, but only 1 byte of "U"
	                        System           and 1 byte of "V"; the color
	                                         information is kept. This totals
	                                         18 bytes or 144 bits of
	                                         information per block. Thus 9
	                                         bits per pixel. This format
	                                         stores its files in a sequence
	                                         of three planes. Each plane
	                                         represents one of the "Y," "V,"
	                                         and "U" color space.
	
	VIDC.MRLE    MSRLE.DRV   -Cinemania 1995  MICROSOFT RUN-LENGTH ENCODING
	=MSRLE.DRV              -Complete
	                        -World of Flight
	                         Baseball Guide  MS video codec used for
	                        -Complete        compressing clean graphic
	                         Basketball      images. It has low CPU overhead,
	                        -Dangerous       but does not handle rapid,
	                         Creatures       complete scene changes. It is a
	                        -Encarta 95-97   device independent bitmap that
	                        -Asimov          involves the basic scheme of
	                        -Wine Guide      compressing multiple,
	                        -Scholastic's    horizontally  adjacent,
	                         Magic School    identical pixels into a run
	                         Bus Explores    encoding (the number of  similar-
	                         the Solar       colored pixels that are side-by-
	                         System          side). These can be stored in 4-
	                        -World of Flight or 8-bit encoding schemes that
	                                         defines an index into the 256-
	                                         color table. This format is slow
	                                         to decode and not widely
	                                         supported.
	
	VIDC.MSVC    MSVIDC.DRV  -Ancient Lands   MICROSOFT VIDEO 1 COMPRESSOR
	=MSVIDC.DRV             -Bookshelf 1994
	                        -Cinemania 1995  A video codec that compresses
	                        -Complete        data quickly, has a low CPU
	                        -Baseball        overhead, and is good for full
	                        -Complete        motion, moderate quality video.
	                         Basketball      Uses a dynamic palette stored in
	                        -Dangerous       the AVI file that enables video
	                         Creatures       clips to attain the appropriate
	                        -Dinosaurs       palette per video file. This is
	                        -Encarta 95-97   the default video driver for
	                        -MS Office       Windows.
	                         Professional
	                         and Bookshelf
	                        -Asimov
	                        -Schubert
	                        -Stravinsky
	                        -Strauss
	                        -Wine Guide
	                        -Scholastic's
	                         Magic School
	                         Bus Explores
	                         the Solar
	                         System
	                        -World of Flight
	
	NOTE: INDEOV.DRV is considered the "umbrella" driver. It is used to point to the
	INDEOV.INI file by the VIDC entries. The INDEOV.DRV then uses the file that is
	needed.
	
	For more information about the Intel Video Driver, contact the following:
	
	  Intel FaxBack: (800) 628-2283 or (916) 356-3105
	  Intel BBS: (916) 356-3600
	  Intel Literature Hotline: (800) 548-4725
	
	
	Additional query words: 1.0 multi media multimedia multi-media homekids mmtitles mmhome
	
	======================================================================
	Keywords          : win31 
	Technology        : kbOfficeSearch kbHomeProdSearch kbHomeMMsearch kbEncartaSearch kbZNotKeyword kbKidsSearch kbEncartaEncycSearch kbAncientLands kbMMStrauss kbMMSchubert kbAsimovSearch kbDangerousCreatures kbDinosaurs100 kbWine100 kbWine100a kbWine200 kbScholasticSolar kbArtGallery kbEncartaEnCyc1996 kbEncartaEnCyc1997 kbEncartaEnCyc1997Del kbMSBSearch
	Version           : :1.0,1.0a,2.0
	
	=============================================================================
	

{% endraw %}
