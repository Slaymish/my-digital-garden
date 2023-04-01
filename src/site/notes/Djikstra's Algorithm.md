---
{"dg-publish":true,"permalink":"/djikstra-s-algorithm/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-04-2023
***
[[COMP Graphs and data structures\|COMP Graphs and data structures]]

# Finding the shortest path

#### Example pseudocode:
```
FindShortestPath(start,goal):
	fringe (PriorityQueue of <node,edge,length-to-node)
	backpointers (Map of nodes to edges)
	put <start,null,0> on the fringe
	while fringe is not empty:
		<node,edge,length-to-node> (remove from fringe)
		if node is not visited:
			visit node
			put <node,edge> into backpointers
			if node = goal:
				return ReconstructPath(start,goal,backpointers)
				
```