---
dg-home: false
dg-publish: true
---
Related: #programming #java 
Contents: [[COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 19-05-2023
***

- If data contains llts of runs of repeated symbols, it may be efficient to store as (count,symbol) pairs

# EG

```
aaabbaaaaaapaa
==
3a2b6ap2a
```

- 1 byte for count (up to 256)
- 1 byte for character

# EG 2

- Could use 6 bits to store black and white image data
- 5 bits for count
- 1 bit to say what is repeated

```
11111111000000001111111111111111

===

010001001100011011
01000 1 00110 0 01101 1
```


[[Lempel-Ziv]]
