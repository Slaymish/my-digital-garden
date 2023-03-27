---
{"dg-home":false,"dg-publish":true,"permalink":"/comp-graphs-and-data-structures/","dgPassFrontmatter":true}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 26-03-2023
***
# Graphs
- Collection of nodes and edges

### Applications
- Places with connections
	- Airports and flights etc
- Entities with relationships
	- Social networks, webpages friends
- States and actions
	- Games, plans


# Kinds of graphs
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



### How connected?
- Sparse Graphs
	- Most pairs of nodes not connected
	- $|edges|<<|nodes|^2$
- Dense Graphs
	- Nodes connected to most other nodes
	- $|edges| \approx |nodes|^2$


***

# Graph Data Structure

Traditional data structures:
- [[Adjacency Matrix\|Adjacency Matrix]]
- [[ Adjacency list\| Adjacency list]]

Object-based data structures:
- Collection of Node objects with lists of neighbours
- Collection of Edges objects with pairs of connections

