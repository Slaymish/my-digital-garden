---
{"dg-publish":true,"permalink":"/a-algorithm/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-04-2023
***

[[COMP Graphs and data structures\|COMP Graphs and data structures]]


- Nodes on fringe are ordered by estimated total path length through this node
	- = length of path from start to this node + estimate of remaining distance
	- (Same as [[Djikstra's Algorithm\|Djikstra's Algorithm]])
- Fringe items must have
	- node
	- previous node or edge (for the backpointers)
	- distance to node from start (needed to compute the distance to the neighbours)
	- total estimated path length


***

# Finding the Shortest Path

```
FindShortestPath(start,goal):
	fringe (PriorityQueue of <node,edge,length-to-node,est-total-path> Ordered by estimate)
	backpointers (Map of nodes to edges)
	put <start,null,0,est(start,goal)> on the fringe
	while fringe is not empty:
		<node,edge,length-to-node,est-total,path> (from fringe)
		if node is not visited:
			visit node
			put <node,edge> into backpointers
			if node=goal:
				return ReconstructPath(start,goal,backpointers)
			for each neigh-edge out of node to a neighbour:
				if neighbour is not visited:
					length-to-neighbour = length-to-node + neigh-edge.length
					est-total-path = length-to-neighbour + est(neighbour,goal)
					add <neighbour, neigh-edge, length-to-neigh, est-total-path> to fringe

```


# When does it work?

- Its the shortest path when following conditions are satisfied

1.  The estimated cost to goal is never greater than the true cost
	- The heuristic estimate must be 'admissible'

2. When we take node off fringe, this must be the shortest path to that node from the start
	- The heuristic estimate must be 'consistent' or 'monotonic'



***

## Admissible heuristic for A*

- Is admissible if it **always** underestimates the remaining cost
	- Overestimating can cause A* to avoid a path (even it its the best)


## Monotonic/Consistent heuristic for A*

- When visiting a node, must be the best path to a node
- To be able to commit to visited nodes:
	- dist-to-X + est(X) ≤ dist-to-X + edge-X-Y + est(Y)
- Consistent heuristic:
	- est(X) - est(Y) ≤ edge-X-Y




