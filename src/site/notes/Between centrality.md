---
{"dg-publish":true,"permalink":"/between-centrality/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 05-05-2023
***

# Betweenness Centrality

- Used to find bottlenecks, and vulnerabilities

Betweenness centrality measures how often a node appears on shortest paths between pairs of other nodes. Nodes with high betweenness centrality are considered "bridges" or "gatekeepers" between different parts of a network.

## Formula

$$C_B(u) = \sum_{s \neq u \neq t} \frac{\sigma_{st}(u)}{\sigma_{st}}$$

Where:
- $C_B(u)$ represents the betweenness centrality of node $u$
- $sigma_{st}$ is the total number of shortest paths from node $s$ to node $t$
- $sigma_{st}(u)$ is the number of those shortest paths that pass through node $u$



