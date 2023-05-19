---
{"dg-publish":true,"permalink":"/lempel-ziv/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 19-05-2023
***

# Lempel-Ziv

- Lossless [[Compression\|Compression]]
- LZ77 = simple compression, using repeated patterns
	- basis for many later, more sophisiticated compression schemes

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
- If no previous apperence `[0,0,symbol]`