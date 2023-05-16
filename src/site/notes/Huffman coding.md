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

[[Compression#Prefix-free Codes\|Prefix-free codes]]

- New nodes added in the order indicated by their letters
- Letters/symbols don't mean anything

Combine lowest two nodes.
Once combined, add the two weights, and combine into a new node with that weight
Add that node back into the list and use as if its the other nodes

## Assigning the Codes

- Assign 0 to left, 1 to right
- 