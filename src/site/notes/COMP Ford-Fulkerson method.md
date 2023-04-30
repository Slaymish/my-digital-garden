---
{"dg-publish":true,"permalink":"/comp-ford-fulkerson-method/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 30-04-2023
***

# Ford-Fulkerson method

Based on:
- [[COMP Residual Graphs\|Residual Graphs]] (a graph that includes [[COMP Flow Network#Reverse Edges\|reverse edges]])
- [[COMP Residual Graphs#Augmentation Path\|Augmentation paths]] (path in a residual graph)
- Cuts



Pseudo-code:
```
FordFulkerson(G,s,t)
Let f(e) = 0 for all edges (flow = 0)
Initialize Residual Graph RG 
	// for every forward edge in G add a reverse edge with capcity 0
maxFlow = 0

Repeat (until RG has no more augmentation paths):
	Find some path P from s to t in RG such c_e>0 for all edges in P
	if P exists
		pathFlow = Bottleneck(P,RG)
		maxFlow = maxFlow + pathFlow
		Output (P,pathFlow) as a augmentation path
		Update RG

Output maxFlow
```

***

# Updating Residual Graph

```
For each edge e = (u,v) thats in P
	f(u,v) = f(u,v) + pathFlow // add flow
	c(u,v) = c(u,v) - pathFlow // reduce capcity

	c(v,u) = c(v,u) + pathFlow // increase capcity in reverse edge
```

[[Edmond-Karp algorithm\|Edmond-Karp algorithm]] is an implementation of [[COMP Ford-Fulkerson method\|Ford-Fulkerson method]] that uses [[Breath-first traversal\|BFS]] for finding augmenting paths.


***

## Finding an Augmentation Path using BFS

```java
BFS(RG,s,t){
	augPath = Arraylist of edges
	q = new queue()
	q.push(s)
	backpointer(v) = null for all v // hashmap/array

	while (!q.isEmpty()){
		current = q.pull()
		for(each outedge of current in RG){
			if (e.toCity != s && backpointer(e.toCity) == null && e.cap != 0)
			{
				backpointer[e.toCity] = e
				if(backpointer[t] != null){
					pathEdge = backpointer[t]
					while(pathEdge != null){
						augPath.add(pathEdge)
						pathEdge = backpointer[pathEdge.fromCity]
					}
					Collections.reverse(augPath)
					return augPath
				}
				q.push(e.toCity)
			}
		}	
	}
	return null
}
```


### Implementing Edmond Karp

With an [[Adjacency Matrix\|Adjacency Matrix]]
- 2d Matrix
- each index will have a pair of values
	- first = edge capacity
	- second = flow through edge

With an [[Adjacency list\|Adjacency list]] 
- Have a node list and a edge list
- Edge list
	- Have a forward edge at even indices
	- And reverse edge at odd
- Node list
	- Contains a list of edge ids originating from node








