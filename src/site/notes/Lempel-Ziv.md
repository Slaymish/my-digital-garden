---
{"dg-publish":true,"permalink":"/lempel-ziv/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 19-05-2023
***

# Lempel-Ziv

- Moves a **cursor** through text one character at a time
- `[offset,length,nextCharacter]` or `[0,0,character]`
- Searches for a match for the *longest possible lookahead*
	- Stops expanding when there isn't a match

- Lossless [[Compression\|Compression]]
- LZ77 = simple compression, using repeated patterns
	- basis for many later, more sophisticated compression schemes

- Key idea:
	- If you find a repeated pattern, replace latter ones by a link to the first

```
a contrived text containing riveting contrast

a contrived text[15,5] ain[2,2]g[22,4]t[9,4][35,5]ast

15 = amount have to go back
5 = how many letters are there
```

## How to Distinguish Pointers from Ordinary Characters

- Store text as triples:
- `[offset,length,symbol]`
- If no previous appearance `[0,0,symbol]`

### To Limit Size of Offset and Length

- Limit the size of window to left of current pos in which we look for a match
- Limit distance ahead we look in the input for a match


- Because we have to keep the same format, we include matches of length 1
- Even though this makes it bigger

### Pseudocode

- Looks for an occurrence of `text[cursor..cursor+length]` in `text[start..cursor-1]`
- Wasteful as we know there's no match before prevMatch, so no point looking there again

```
cursor <- 0; 
windowSize <- 100;
while cursor < text.size:
	length <- 1;
	prevMatch <- 0;
	loop:
		match <- stringMatch( text[cursor.. cursor+length],
			text[((cursor<windowSize) ? 0 : cursor-windowSize) .. cursor])

		if match succeeded then:
			prevMatch <- match
			length <- length + 1
		else:
			output( [a value for prevMatch,
					length - 1, text[cursor+length -1]])
			cursor <- cursor + length
			break;
	endLoop
```

# Decompression

```
[0,0,a][0,0,_][0,0,c][0,0,o]
```

## Pseudocode

```
cursor <= 0
for each tuple:
	if [0,0,ch] : output[cursor++] <+ ch
	elif [offset,length,ch]:
		for j = 0 to length-1
			output[cursor++] <= output[cursor-offset]
		output[cursor++] <= ch
```

***

### General Notes

- Encoding is expensive, decoding is cheap
- Improvements
	- Could use two types of output value:
		- (offset,length) pair for repeated sequence,
		- character for non-repeat
		- How to distinguish them?
- Can be used in conjunction with [[Huffman coding\|Huffman coding]]