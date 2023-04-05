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
- uses [[Iterative Graph Traversal#^4cc5ce\|ReconstructPath()]]
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
			for each edge out of node to a neighbour:
				if neighbour is not visited:
					length-to-neighbour = length-to-node + edge.length
					add <neighbour,edge,length-to-neighbour> to fringe
				
				
```

- Check if node is the goal when we *remove* from fringe, not add


***

# Finding **All** Shortest Paths:

### Ex PseudoCode
```
FindShortestPaths(start,goal):
	fringe (PriorityQueue of <node,edge,length-to-node)
	backpointers (Map of nodes to edges)
	put <start,null,0> on the fringe
	while fringe is not empty:
		<node,edge,length-to-node> (remove from fringe)
		if node is not visited:
			visit node
			put <node,edge> into backpointers

			for each edge out of node to a neighbour:
				if neighbour is not visited:
					length-to-neighbour = length-to-node + edge.length
					add <neighbour,edge,length-to-neighbour> to fringe
					
	return backpointers (= all shortest paths)
```


***

## Cost of Djikstra's algorithm?
*If a graph has N nodes and E edges*

**Identify the most expensive line**
```
while fringe is not empty:
	..
	for each edge out of node to a neighbour:
		..
		add <neighbour,edge,length-to-neighbour> to fringe
		
```


$= O((E+N) \ Log N)$


***

## Problems
- If we want **all** shortest paths
	- **Djikstra is best**
	- Never backtracks and every iteration adds a path to the answer (greedy)
- If we want the shortest path to a goal
	- **Djikstra is wasteful**
	- Spends time building paths to useless nodes (not the goal)

- To be better
	- Should combine length of path to here AND estimate of remaining dist
		- Biases the choice towards nodes that are on the way to the goal
	- This is [[A* Algorithm\|A* Algorithm]]
