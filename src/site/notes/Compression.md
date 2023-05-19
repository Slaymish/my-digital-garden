---
{"dg-publish":true,"permalink":"/compression/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-05-2023
***

# Lossless

- Want to store data in a smaller size, while not changing any of the data
- Only possible if there is *redundancy* in the original

# Lossy

- For large file types, usually viewed by humans
- Can recover original, with small amount of errors

## Problem

- Given a set of **symbols** (characters, numbers, colours etc)
- Encode them as **bit strings**
	- Use a separate code for each symbol
- Try to minimise the total number of bits
- [[Huffman coding\|Huffman coding]]
	- Widely used (JPEG/MP3 as a back-end)

After compression, we often add extra bits (redundancy) so we can detect errors

# Equal Length Codes

- Use same number of bits for every symbol to be encoded
- With $N$ bits, we can have $2^N$ different codes
- For $N$ different symbols, need $log_2N$ bits per symbol
	- 10 numbers, length = 4
	- 26 letters, length = 5

## Digits

| 0    | 1    | 2    | 3    | 4    | 5   |
| ---- | ---- | ---- | ---- | ---- | --- |
| 0000 | 0001 | 0010 | 0011 | 0100 | 0101    |

4 bits (from 8)
$4/8 = 50\%$ compression rate

## Letters

| a    | b    | c    | d    | e    | f    | z     |
| ---- | ---- | ---- | ---- | ---- | ---- | ----- |
| 00001 | 00010 | 00011 | 00100 | 00101 | 00110 | 11010 |

5 bits (from 8)
$5/8 = 62.5\%$ compression rate


How many bits needed?
- 26 symbols = 5bits
- Better than 8bits (uncompressed)

# Variable Length Codes

Eg: String `aabajabaab`

| Symbol | Occurrence |
| ------ | ---------- |
| a      | 50%        |
| b-c    | 15%        |
| d-e    | 5%         |
| f-j    | 2%         |

```
using 4 bits each as 10 letters
Fixed: 0000 0000 0001 0000 1001 etc // zeros redundant

using 13 bits
Variable: 0 0 1 0 1010 etc 
// can't really decode, cus don't know boundries
```

## Possible Fix

- Use 0 as a '[[Sentinel Bit\|Sentinel Bit]]' to mark the end of a code
- Then only use 1's for the code itself
- Not the best way

## Prefix-free Codes

- No code is the prefix of another code

| a   | b   | c    | d     | e     | f     | g     |
| --- | --- | ---- | ----- | ----- | ----- | ----- |
| 0   | 10  | 1100 | 11101 | 11100 | 11111 | 11010 |

### Implementing with a [[Year 1/COMP103/Trees#^fdf183\|Binary Tree]]

- Use leaves as symbols
- Balanced tree gives equal length codes
- Linear tree is like using a [[Sentinel Bit\|Sentinel Bit]]
- More frequent symbols at the top, less frequent at bottom

#### To Build

This is [[Huffman coding\|Huffman coding]]

##### Combine

- Build tree from bottom-up, combining nodes with smallest frequencies
- Start with a leaf for each symbol, labelled with its frequency
- At *each* step, add new node to queue that's sum of the two nodes with smallest frequencies, with those nodes as children. 
- Stop *when* all nodes are combined into a single tree

##### Assign

- Once you have the tree, assign the code to each letter
- Traverse from root
- Parent code + 0 to left child
- Parent code + 1 to right child

## Shannon, and Information Theory

### Source Coding Theorem

- The *optimal* code length for a symbol is

$$\log _2P$$

- Where $P$ is the probability of the input symbol. 
- The **average** of this, over the while alphabet, is call the **entropy**, $H$
- If $P$ was 'flat' (all letter equal $p$), $H=4.74$ bits
- With actual $P$, it drop a bit to $4.2$ bits/char

But that ignores the fact that its a *sequence*

### Predictable Structure -> Shorter Codes

- Diagram/bigram and trigram? The most common are:

| Diagram | Trigram |
| ------- | ------- |
| EN      | ENT     |
| RE      | ION     |
| ER      | AND     |
| NT      | ING     |
| TH      | IVE     |

- Using trigrams drop entropy to about $2.6$ bit/char
- If you go to **n-gram**, with n >>
	- You get about $0.6 - 1.3$ bit/char!!

