---
{"dg-publish":true,"permalink":"/cycles/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 06-05-2023
***

# Cycle in Graphs

A cycle is a non empty path which begins and ends at the same vertex

## Simple Cycle

Is a cycle with no repeated vertices except for the beginning and ending vertex

# Examples

$C_1=(V,X,Y,W,U,V)$ is a simple cycle
$C_2=(U,W,X,Y,W,V,Y)$ is **not** a simple cycle


***

# Deadlock

Where something depends on something that depends on that thing etc

A set of task are dependent on each other in a circular form - *circular wait*

## Operating Systems

Once a resource has been allocated to a [[NWEN Processes\|process]], there's no simple mechanism by which the system can take the resource back, unless the process voluntarily gives it up or the system admin kills the process

This situation can lead to a **deadlock**

A set of processes are deadlocked when each process or thread is waiting for a resource to be freed which is controlled by another process


***

# Cycle Detection

## In a Undirected Graph

### [[Depth-First traversal\|DFS]]

- We start from a node
- Then explore other nodes as long as we can go along a path
- When reaching the end of the path, we do a backtrack up to the point where we began from and repeat the cycle until we have visited all nodes

### Example

List of nodes, each node has list of edges

`Map<Node,List<Node>>`

- When all nodes have been visited, that's when you stop

- If there's an edge in the graph, but not the DFS path, **there's a cycle**
	- If node is an ancestor, there's a cycle


[[Back edge\|Back edge]]: Edge which is missing in the DFS tree but present in the graph

Steps:
1. Start DFS traversal
2. Keep track of parent of the node being visited
3. If you find a node that has already been visited but is not the parent of the current node being visited, there's a cycle

```java
public void DFS(Node toSearch, Node parent, Set<Node> visited){
	
}
```




#### Complexity

- Same as [[Depth-First traversal\|Depth-First traversal]]
- [[Adjacency list\|Adjacency list]] implementation: $O(V+E)$
- [[Adjacency Matrix\|Adjacency Matrix]] implementation: $O(V^2)$



***

## BFS Vs DFS

- BFS explores all children of node before exploring children 



