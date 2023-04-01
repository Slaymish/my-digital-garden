---
{"dg-publish":true,"permalink":"/object-oriented-graphs/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-04-2023
***
[[COMP Graphs and data structures\|COMP Graphs and data structures]]

- Graph has a Collection of Nodes
```java
private Collection<Node> allNodes;
```
- Also maybe a collection of edges
```java
private Collection<Edge> allEdges;
```


- Could contain a HashMap from Pairs of Nodes to Edges
```java
HashMap<Pair<Node,Node>,Edge> allEdges;
```

<p align="center">
Collections can be Lists or Sets
</p>

***


### Nodes Class
- Contains collection of edges
```java
private Collection<Edge> edges;
```
- Or two if directed graph
```java
private Collection<Edge> outgoing;
private Collection<Edge> incoming;
```


## Edge Class
- Contains two nodes
```java
private Node from;
private Node to;
```



***

# Wellington Public Transport Map
*Same as assignment 2*

- Complex Graph structure
	- Directed
	- Multi-graph
	- Lots of information on nodes and edges
	- Additional structure ('trips'), kinds of edges

For assignment:
- Build the graph structure edges and neighbors
- Find strongly connected subgraphs
- Find shortest paths (distance or time)
- Find articulation points (breakages)

