---
{"dg-publish":true,"permalink":"/comp-test-4/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-06-2023
***

# Test 4

## Algorithms

- [x] [[KMP Algorithm\|KMP Algorithm]] - [[String Search\|String Search]] but with [[KMP Algorithm#Building the Jump Table\|Jump Table]]
- [x] [[Lempel-Ziv\|Lempel-Ziv]] - `[offset (to go back),length,nextCharacter]` or `[0,0,character]`
- [x] [[Huffman coding\|Huffman coding]] - **Best** set of codes, given frequency of all symbols ([[Binary tree\|Binary tree]])
- [x] [[Fast Fourier Transform\|Fast Fourier Transform]]
- [x] [[String Search#Brute Force Search\|Brute Force Search]]

## Things Covered

- [[Compression\|Compression]]
	- [[Huffman coding\|Huffman coding]]
	- [[Lempel-Ziv\|Lempel-Ziv]]
	- [[Arithmetic Coding\|Arithmetic Coding]]
- [[String Search\|String Search]]
	- [[KMP Algorithm\|KMP Algorithm]]
- [[Fast Fourier Transform\|Fast Fourier Transform]]

# String Search

## Brute Force Search

- Worst case: $O(mn)$ 

## KMP Algorithm

- Time to build jump table $O(n)$
- Time to run KMP $O(m)$
- Total: $O(m+n)$

**When fail**:
- Check sub string before letter it failed on
- If there's a suffix that's also a prefix

# Compression

## Huffman Coding

- Combine lowest two nodes.
- Once combined, add the two weights, and combine into a new node with that weight
- Add that node back into the list and use as if its the other nodes
- Repeat until all combined into one [[Binary tree\|Binary tree]]

## Lempel-Ziv

 If you find a repeated pattern, replace latter ones by a link to the first
`[offset (to go back),length,nextCharacter]` or `[0,0,character]

## Arithmetic Coding

- Goes letter by letter, appending more to the current probabilities code when there's a new partition

- Still based on the frequency of symbols
- Though reads as stream (whole sequence) instead of [[Huffman coding\|Huffman coding]] or similar
- Uses probability of a **whole sequence**
- Represents it as a [[Binary Fraction\|Binary Fraction]]

# FFT

## Complexity

$$O(nLogn)$$
- $n$ is the closest power of 2 to the degree of the polynomial
- [[FFT\|FFT]] decreases it from $O(n^2)$ by having pairs of positive/negative numbers
	- Because of Divide and conquer strategy

## Use of Complex Numbers in FFT

- Points are often pairs of positive/negative numbers
- Represented using the Nth roots of unity
- Each **Nth Root of unity is a complex number**
	- Whose powers cycle through values on the unit circle in the complex plane

Nth roots of unity in exponential form:
$W=e^{2\pi i/n}$

- Real part = cosine function
- Imaginary part = sine function

Rotates around a unit circle in the complex plane





