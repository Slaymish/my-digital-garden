---
dg-home: false
dg-publish: true
---
Related: #programming #java 
Contents: [[COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 26-03-2023
***

# Graphs

- Collection of nodes and edges

## Applications

- Places with connections
	- Airports and flights etc
- Entities with relationships
	- Social networks, webpages friends
- States and actions
	- Games, plans

# Kinds of Graphs

- Directed or undirected
	- Symmetric or one-way
	- Line with no arrows = undirected
	- With arrows = directed
- Single or multi-graph
	- Can there be two edges between a pair of nodes
	- Eg airports - multiple dests from one source
- Do *edges* have information attached
	- Weights/lengths/labels
- Bipartite graphs
	- Two kinds of nodes
	- Edges between types
		- eg supervisors and projects

## How Connected?

- Sparse Graphs
	- Most pairs of nodes not connected
	- $|edges|<<|nodes|^2$
- Dense Graphs
	- Nodes connected to most other nodes
	- $|edges| \approx |nodes|^2$


***

# Graph Data Structure

Traditional data structures:
- [[Adjacency Matrix]]
- [[ Adjacency list]]

[[Object Oriented Graphs\|Object-based data structures]]:
- Collection of Node objects with lists of neighbours
- Collection of Edges objects with pairs of connections


***

# Graph Algorithms

**Algorithm 1:** [[Depth-First traversal]]

**Algorithm 2:** [[Iterative Graph Traversal\|Iterative]]

**Algorithm 3 (shortest path):** [[Djikstra's Algorithm]]

**Algorithm 4 (shortest path):** [[A* Algorithm]]


***

## Connected Components (undirected)

^dabfa7

```
ConnectedComponents(graph)
	comptNum = 0;
	for each node in nodes;
		if nodes is not visited:
			traverse(node,comptNum)
			comptNum++

traverse(node,comptNum)
	vist node
	node.compt = comptNum
	for each neighbour of node:
		if neighbour is not visited:
			TraverseGraph(neighbour,comptNum)


// all nodes that have the same component num, are directly connected
```