---
{"dg-publish":true,"permalink":"/huffman-coding/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-05-2023
***

# Huffman Coding

- Generate the **best** set of codes, given frequencies/probabilities on all the symbols
- Creates a [[Binary tree\|Binary tree]], which is used to construct the codes


[[Compression#Prefix-free Codes\|Prefix-free codes]]

- New nodes added in the order indicated by their letters
- Letters/symbols don't mean anything

## [[Compression#To Build\|To build]]

- Combine lowest two nodes.
- Once combined, add the two weights, and combine into a new node with that weight
- Add that node back into the list and use as if its the other nodes

### Pseudocode

```
while more than one node in queue: (> 1 tree)
	remove the top two nodes
	create a new tree node with these nodes as children
		node frequency = sum of the two nodes
	add new node to the queue
```

- To decode, need table of the codes used
- If we label edges of tree with 0's and 1's, can decode


- When storing/transmitting a compressed file, we need to include the tree for decompressing
	- Can reduce efficiency

### OR

- use a *standard frequency table*, not based on the particular file, for code


- 


