# S7-PLC_SHA1
## SHA1 encryption FC for Siemens PLC S7-1200 and S7-1500

Sha1 is an cryptographic algorithm that takes a string of any length and reduces it to a unique fixed length string. 
In this implmementation the string length is limited to a maximum length of 254 characters (String[254] - 2032 bit).

depending on the input "inputmode" different inputformats are used
1   Message is used as Bytes
2   Message is used as String

depending on the input "outputmode" different outputformats are available
1   The digest ouput is the final hash value as a string of H0 - H4 (Array [0..19] of Byte)
2   The hexdigest output is the final hash value as a hexadecimal string of H0 - H4 (40 bytes string)
3   Both 1 and 2

For further informations take a look at RFC 3174
Sha1 is not considered anymore as a secure hash type!

	-Step 00: Initialize variables H0 - H4
	-Step 01: Convert message to Bytes
	-Step 02: Appending padding Bits
	-Step 03: Append 64 Bit containg the original message length in Bits
	-Step 04: Get the amount of chunks data (chunk = 512 Bit)
	-FOR every chunk do Step 05 - Step 09:
	    -Step 05: Break the chunk into 16 DWords
	    -Step 06: Extend chunk to 80 DWords
	    -Step 07: Initialize variables A - E
	    -Step 08: Do some bitwise operations on the 80 chunk DWords
	    -Step 09: Save the chunk's hash to result for the next chunk
	-Step 10: Produce "digest"
	-Step 11: Produce "hexdigest"
  
![SHA1](https://github.com/marvin-mangold/S7-PLC_SHA1/assets/10088323/668d7fba-afee-49ea-b984-342b83b50892)
