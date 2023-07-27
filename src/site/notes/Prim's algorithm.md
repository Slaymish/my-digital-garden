---
{"dg-publish":true,"permalink":"/prim-s-algorithm/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 11-05-2023
***

# Prim's Algorithm

- Results in a **Minimum [[Spanning Trees\|Spanning Trees]]**
- Connected, undirected graph with edge weights

## Steps

1. Pick any node to start on (A)
2. Add A to visited list
3. Examine all nodes reachable from A
4. Choose smallest edge that connects to an unvisited node (B)
5. Then look at all nodes reachable from A&B
6. Choose smallest edge available that connects to an **unvisited** node

## Time Complexity

- [[Adjacency Matrix\|Adjacency Matrix]] -> $O(v^2)$
- [[Adjacency list\|Adjacency list]] -> $O(VlogV + ElogV)$
