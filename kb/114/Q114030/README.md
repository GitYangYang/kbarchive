---
layout: page
title: "Q114030: PC WRmt: AT&amp;T Credit Card Calling Modem Script"
permalink: /kb/114/Q114030/
---

## Q114030: PC WRmt: AT&amp;T Credit Card Calling Modem Script

{% raw %}

	Article: Q114030
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail Remote for Windows, version 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Version 3.2 of Microsoft Mail Remote for Windows allows you to use a credit card
	modem script to place a call via the AT&T phone system and credit any
	charges to the AT&T credit card. Below is the CALL section of the script. To
	use this script, copy the information between the BEGIN HERE and STOP HERE
	comments and paste it into the same part of the script for the modem you are
	using.
	
	  ; BEGIN HERE
	
	       $ret = 8               ; Set default ret code to "no answer"
	
	       clearrsp               ; Clear the response buffer
	
	       echo 0                 ; Do not display phone number
	
	  ; If this script is specified in the phone number field, the
	  ; initialize script in the default script file may have turned off the
	  ; speaker. The following commands will turn the speaker back on for
	  ; Hayes compatible modems:
	  ;
	       sendln "ATM1"           ; Turn speaker on
	       waitrsp 1               ; Get the response back from the modem
	
	  ; In order to make credit card dialing work, the modem being used must
	  ; support the ";" dial modifier. This character returns the modem to
	  ; command state after the dial string is sent, allowing us to proceed
	  ; with further processing. The operator is prompted to press a key.
	  ; When he does, send another dial string. This time the dial string is
	  ; the credit card number.
	  ; Remember that the phone number must be in the form:
	  ;               0 - area code - number
	
	       ; Standard number to call to get into AT&T
	       sendln "ATD" + dial_mode + "9,10-288-0" + ";"
	
	       wait 2
	
	       ; ### = phone number to call, should be EXTERNAL.EXE
	       sendln "ATD" + dial_mode + "###-###-####" + ";"
	
	       echo 1                 ; Turn echo back on
	
	       display 'Press any key when you hear the "bong"...'
	
	  ; Wait until a key is struck
	  operator_wait_loop:
	       getkey
	       if (key = 0)
	         goto operator_wait_loop
	
	  ; Now send the credit card number. You will have to replace the number
	  ; used here with your credit card number.
	
	       ; Do not display credit card number
	       echo 0
	
	       ; Send the AT&T credit card number
	       sendln "ATD" + dial_mode + "$$$-$$$-$$$$-$$$$"
	
	       ; Turn echo back on
	       echo 1
	
	       ; Should get "OK" from modem
	       waitrsp 2
	       if (response != "0^M")
	         return $ret
	
	       ; Wait until the modem responds (max 2 minutes)
	        waitrsp 120
	
	  ; STOP HERE
	
	  ; The section that follows is specific to the modem used. For example,
	  ; this section is from the Multitec modem script, MULTITEC.MDM:
	
	          if ("12" isin response)
	            {
	            display ">>> CONNECT 9600 <<<"
	            $ret = 12
	            }
	          else if ("11" isin response)
	            {
	            display ">>> CONNECT 4800 <<<"
	            $ret = 11
	            }
	          else if ("10" isin response)
	            {
	            display ">>> CONNECT 2400 <<<"
	            $ret = 10
	            }
	          else if ("7" isin response)
	            {
	            display ">>> BUSY <<<"
	            $ret = 7             ; busy
	            }
	          else if ("5" isin response)
	            {
	            display ">>> CONNECT 1200 <<<"
	            $ret = 5
	            }
	          else if ("3" isin response)
	            {
	            display ">>> NO CARRIER <<<"
	            $ret = 8             ; no answer or no connect
	            }
	          else if ("1" isin response)
	            {
	            display ">>> CONNECT 300 <<<"
	            $ret = 1
	            }
	
	          if ("R" isin response)
	            display ">>> MNP RELIABLE CONNECTION <<<"
	
	          if ("L" isin response)
	            display ">>> LAPM RELIABLE CONNECTION <<<"
	
	          if ("C" isin response)
	            display ">>> DATA COMPRESSION ENABLED <<<"
	
	          return $ret            ; return connect baud rate to application
	
	Additional query words: 3.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailRemote320
	Version           : WINDOWS:3.2
	
	=============================================================================
	

{% endraw %}
