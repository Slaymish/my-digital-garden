---
{"dg-publish":true,"permalink":"/comp-monopoly-and-oligopoly/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 05-05-2023
***

# Comp Monopoly and Oligopoly

## [[Edmond-Karp algorithm\|Edmond-Karp algorithm]] Example

**Step 1:**
- Initialise residual graph
	- Adjacency list of edges
	- List of nodes, each node has list of indices of outgoing edges
- Set maxFlow = 0

**Step 2:**
- Find augmentation path 
	- [[Breath-first traversal\|Breath-first traversal]]
	- Use backpointers
- Add to flow
	- pathFlow = min flow of all edges in augmentation path
- Update residual graph
	- for edge edge in the augmentation path
		- increase flow by bottleneck
		- decrease capacity by bottleneck
		- increase capacity in the reverse edge by bottleneck
	- How to reverse an edge
		- Array representation
			- `G[v][u]` will become `G[v][u]`
		- Adjacency list representation
			- If edge array list stores an edge at an **even** index $i$
				- Then $i+1$ is the reverse edge
			- Otherwise its reverse edge is at $i-1$

# Centrality

Relates to importance/ranking of nodes

## Use Cases

- Find accounts through which most of the money flows

## Centrality Algorithms

- [[Degree centrality\|Degree centrality]]
	- Baseline metric
	- Measures the number of relationships a node has
- [[Closeness centrality\|Closeness centrality]]
	- How central a node is to the group
	- Calculates which nodes have the shorest paths to all other nodes
- [[Between centrality\|Between centrality]]
	- Finding control points
	- Measures the number of shorest paths that pass through a node
- [[Page Rank\|Page Rank]]
	- Overall influence
	- Estimates a current nodes importance from its linked neighbours and their neighbours (used by google for ranking web pages)


![SCR-20230505-pyl.png](/img/user/SCR-20230505-pyl.png)




