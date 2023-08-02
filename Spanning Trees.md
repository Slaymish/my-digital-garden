---
dg-home: false
dg-publish: true
---
Related: #programming #java 
Contents: [[COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 11-05-2023
***

# Spanning Trees

## Muddy City Problem

- Best routes connects all houses, but uses as few paving stones as possible
- Different to shortest path

### Given a Connected, Undirected, Weighted Graph

- A spanning tree is a subgraph that contains **all the nodes** but has no [[Cycles]] (is a tree)


- **Every** connected graph has at least one spanning tree

#### Theorem

Any tree with $n$ verts has $n-1$ edges (for a connected graph)

Proof (by induction)


***

## Via [[Depth-First traversal]]

- DFS reaches each node
- We add one edge to connect an unsivisted node to the already visited nodes
- **Order affects results**


If unweighted graph, can just run [[Depth-First traversal\|DFS]] to find [[Spanning Trees\|Spanning tree]]

```
spanning_tree_dfs(Graph G){
	for each node i:
		i.marked = false; // mark all nodes as unvisited

	for some node i: f(i);
}
f(Node i){
	i.marked = true;
	for each j adjacent to i: // nodeList.get(i).forEach()
		if(!j.isMarked){
			add(i,j) // to output 
			f(j);
		}
	}		
}
```






