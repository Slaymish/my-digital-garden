---
{"dg-home":false,"dg-publish":true,"permalink":"/adjacency-matrix/","dgPassFrontmatter":true}
---

Related: #programming #java [[COMP Graphs and data structures\|Graphs]]
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 26-03-2023
***

- Use an *array* to represent info about nodes
- Use integers 0...n-1 to represent each node

```java
private Node[] nodes;
```

- Use a 2D matrix to represent the graph
```java
private int[] edges;
```

- Number of rows and columns = number of nodes
- $M_{ij} = 1$ if theres an edge from node i to node j
- $M_{ij}=0$ (blank) otherwise


