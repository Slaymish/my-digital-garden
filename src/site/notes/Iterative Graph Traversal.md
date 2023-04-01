---
{"dg-publish":true,"permalink":"/iterative-graph-traversal/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-04-2023
***

[[COMP Graphs and data structures\|COMP Graphs and data structures]]


## Example Pseudo-code
```
TraverseGraph(startNode):
	Declare 'fringe' (Stack/Queue)
	put startNode on the fringe
	while fringe.notEmpty():
		Declare node (remove from fringe)
		if node is not visited:
			visit node
			process node
			for each neighbour of node:
				if neighbour is not visited:
					add neighbour to fringe
```

- Fringe = Stack/Queue
	- Nodes that have been 'seen' but not yet processed
	- If Stack - [[Depth-First traversal\|Depth-First traversal]]
	- If Queue - [[Breath-first traversal\|Breath-first traversal]]
	- can also use PriorityQueue
- Non recursive


## Example BFS java code:
```java
public void traverseGraph(Node start){
	Set<Node> visited = new HashSet<Node>();
	Queue<Node> fringe> = new Queue<Node>(); 
	fringe.offer(start);
	while(!fringe.isEmpty()){
		Node node = fringe.poll();
		if(!visited.contains(node)){
			visited.add(node);
			process(node);
			for(Node neighbour : node.getNeighbours()){
				if(!visited.contains(neighbour)){
					finge.offer(neighbour);
				}
			}
		}	
	}
}
```


***


# Finding a Path

- Use priority queue
	- Ordered by shortest straight-line distance from node to goal

### Example Pseudocode
```
FindPath(start,goal):
	fringe (PriorityQueue)
	put start on the fringe
	while fringe not empty:
		node (from fringe)
		if node is not visited:
			visit node
			if node=goal:
				return the path to node (See below for how)
			for each neighbour of node:
				if neighbour is not visited:
					add neighbour to fringe

```


## Keeping track of the path

- Need to have 'backpointers'
	- Records how we got to a node

- Use a Map from node to prev node


## Storing Paths

```
FindPath(start,goal):
	fringe (PriorityQueue [of node,prev,edge etc])
	backpointers (Map of nodes to prev node)
	put (start,null,null) on fringe
	while fringe not empty:
		(node,prev,edge..) (remove from fringe)
		if node is not visited:
			visit node
			put (node,prev) in backpointers
			if node=goal:
				return backpointers
			for each edge out of node to a neighbour:
				if neighbour is not visited:
					add(neighbour,node,edge...) to fringe

```

- If edges directed contain from/to nodes, can only put edge in fringe



## Reconstructing Paths from BackPointers



When backpointers is a Map<node,prev>:
```
ReconstructPath(start,goal,backpointers)
	path (list of nodes)
	add goal to path
	node  (goal)
	while node != start:
		node (backpointers.get(node))
		add node to path
	reverse path
```

When backpointers is a Map<node,edge>:
```
ReconstructPath(start,goal,backpointers)
	path (list of edges)
	node (goal)
	do
		edge (backpointers.get(node))
		add edge to path
		node (edge.from)
	until node = start
```


***

## How to find the Shortest Path

- Assume edges have a length
- Order PriorityQueue by length of path to node on the fringe
- Limited version of [[Djikstra's Algorithm\|Djikstra's Algorithm]]
	- Djikstra's finds shortest paths to ALL nodes (not just goal)

