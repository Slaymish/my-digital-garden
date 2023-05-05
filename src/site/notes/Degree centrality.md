---
{"dg-publish":true,"permalink":"/degree-centrality/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 05-05-2023
***

# Degree Centrality

Degree centrality measures the importance of a node based on its number of connections (edges). In other words, a node with a high degree centrality has more connections with other nodes.


- Count the num of incoming and outgoing relationships from a node
- Captures the immediate reach


***



## Formula

For an undirected graph:

$$C_D(u) = \frac{deg(u)}{n-1}$$

For a directed graph:

$$C_D^{in}(u) = \frac{indeg(u)}{n-1}$$
$$C_D^{out}(u) = \frac{outdeg(u)}{n-1}$$

Where:
- $C_D(u)$ represents the degree centrality of node $u$
- $deg(u)$ represents the degree (number of edges) for node $u$
- $indeg(u)$ represents the in-degree (number of incoming edges) for node $u$
- $outdeg(u)$ represents the out-degree (number of outgoing edges) for node $u$
- $n$ is the total number of nodes in the graph

