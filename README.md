# Blowfish #

In this repo I have attempted to recreate the Blowfish encryption algorithm in python.

I did this to better understand the Blowfish algorithm and to improve my abilities with python. If you want to use this algorithm in an production I implore you not to use this implementation but instead look for something written by an actual expert. Otherwise I hope this repo can help you understand the core algorithm.

### Algorithm description ###

Blowfish is a block cypher which encrypts data 64 bits at a time. It works using bitwise operations and substitution boxes. 

The key length is between 32 and 488 bits. This key is XORed with a binary representation of the digits of &pi; in order to generate entropy within the key. &pi; is used in order to make sure there are no shenanigans when generating randomness in the key. This also can be said to introduce a problem with Blowfish in that every time it is used with a new key an extra XOR operation is required. 

The encryption of a 64 bit block involves first splitting it into two 32 bit segments, a left side (L) and a right side (R). These are then put through the encryption scheme as shown below.

<p align="center">
<image src='./images/blowfish_full_algorithm.png' width="800px;"></image>
</p>

This diagram shows the structure of the first round of the algorithm, with the next 15 rounds being implied, followed by a whitening step. Each of the 16 steps uses a 32 bit segment of the generated key with the last two segments of the key being used by the whitening step. 

The left side of the block is XORed with the key segment for the round and the result is both conserved and put through the F-block with the result from the F-block being XORed with the right side of the key. At the end of this process the two halves of the block are swapped and the process is repeated until it has been performed the proscribed number of times. Finally the sides are XORed with the final segments of the key, recombined and returned as the encrypted text.

The F-block is a function which contains substitution boxes (S-boxes), XOR functions and modulo additions. This process is shown below:

<p align="center">
<image src='./images/F-block_diagram.png' width="500px;"></image>
</p>

In the F function the 32 bit word is split into 4 8 bit parts. Each of these 8 bit sections are passed trough substitution boxes and the resulting 32 bit words are combined in the manner shown in the diagram. The resulting 32 bit word is the result from the F-function.

In order to decrypt this information it is passed through the same encryption scheme except that P1->P18 are used in reverse order.


## Important note ##

I am some guy in a room. You should never use the code here for real encryption purposes. I hope it will help you understand the principals of Blowfish encryption but this has not been checked by anyone with any real expertise or training in cryptography.

### Sources ###

* https://en.wikipedia.org/wiki/Blowfish_(cipher)
* https://www.schneier.com/academic/blowfish/
* https://www.splashdata.com/splashid/blowfish.htm
