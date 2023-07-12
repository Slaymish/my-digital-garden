---
{"dg-publish":true,"permalink":"/closeness-centrality/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 05-05-2023
***

# Closeness Centrality

- Indicates how close a node is to all other nodes in the network
- Calculated as the reciprocal of the sum of the length of the shortest paths between the node and all other nodes in the graph

Closeness centrality measures how close a node is to all other nodes in the graph. A node with high closeness centrality is "close" to many other nodes and can potentially reach them faster.

## Formula

$$C_{norm}(u) = \frac{n - 1}{\sum_{v=1}^n d(v, u)}$$

Where:
- $C_C(u)$ represents the closeness centrality of node $u$
- $d(v, u)$ is the shortest path distance between nodes $v$ and $u$