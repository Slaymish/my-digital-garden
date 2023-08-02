---
dg-home: false
dg-publish: true
---

# Adjacency Matrix

Related: #programming #java [[COMP Graphs and data structures\|Graphs]]
Contents: [[COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 26-03-2023
***

- Symmetric = symmetric across diags (undirected graph)


**Two numbers representing the nodes**

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
- $M_{ij} = 1$ if there's an edge from node i to node j
- $M_{ij}=0$ (blank) otherwise


- Can't deal with multi-graphs


***

## Time Complexity

- Assume simple graph
	- At most one edge between each pair of nodes, with N nodes and E edges
	- typically $N < E < N^2$

2D adjacency matrix
- Requires $O(N^2)$ of memory space

### Time Cost

- Find all nodes
	- $O(N)$
- Find all edges
	- $O(N^2) = O(E)$
	- Bad for sparse graphs
- Find all outgoing edges of a node
	- $O(N)$
- Find all incoming edges of a node
	- $O(N)$
- Find all outgoing node neighbours
	- $O(N)$
- Find all incoming node neighbours
	- $O(N)$
- Check if there is an edge between two nodes
	- $O(1)$

***

For **large sparse graphs**, don't use adjacency matrices
