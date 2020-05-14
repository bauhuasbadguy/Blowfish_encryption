# Blowfish #

In this repo I have attempted to recreate the Blowfish encryption algorithm in python.


Blowfish is a block cypher which encrypts data 64 bits at a time. It works using bitwise operations and substitution boxes. 

The key length is between 32 and 488 bits. This key is XORed with a binary representation of the didgets of &pi; in order to generate entropy within the key. &pi; is used in order to make sure there are no schnanigans when generating randomness in the key. This also can be said to introduce a problem with Blowfish in that every time it is used with a new key an extra XOR operation is requrired. 

The encryption of a 64 bit block involves first splitting it into two 32 bit segments, a left side (L) and a right side (R). These are then put through the encryption scheme as shown below

DIAGRAM OF OVERALL SCHEME HERE

<p align="center">
<image src='./blowfish_full_algorithm.png' width="800px;"></image>
</p>

The F block in this diagram represents a F-Function which is shown in this diagram

DIAGRAM OF F-BLOCK

<p align="center">
<image src='./F-block_diagram.png' width="500px;"></image>
</p>

In this diagram we can see the s-boxes. These are substitution boxes that take in an 8-bit index and return the desired substitution.


In order to decrypt this information it is passed through the same encryption scheme except that P1->p18 are used in reverse order.



## Important note ##

I am some guy in a room. You should never use the code here for real encryption purposes. I hope it will help you understand the principals of Blowfish encryption but this has not been checked by anyone with any real expertise or training in cryptography.

### Sources ###

* https://en.wikipedia.org/wiki/Blowfish_(cipher)
* https://www.schneier.com/academic/blowfish/
* https://www.splashdata.com/splashid/blowfish.htm

