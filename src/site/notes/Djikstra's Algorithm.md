---
{"dg-publish":true,"permalink":"/djikstra-s-algorithm/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-04-2023
***
[[COMP Graphs and data structures\|COMP Graphs and data structures]]

# Finding the Shortest Path

## Example Pseudocode:

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

## Ex PseudoCode

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

# Cost of Djikstra's Algorithm?

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

# Problems

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


***

## Example Code:

```java
public List<Node> findShortestPath(Node start, Node goal) {
    PriorityQueue<NodeEdge> fringe = new PriorityQueue<>();
    Map<Node, Edge> backpointers = new HashMap<>();
    Set<Node> visited = new HashSet<>();
    fringe.add(new NodeEdge(start, null, 0));
    
    while (!fringe.isEmpty()) {
        NodeEdge nodeEdge = fringe.poll();
        Node node = nodeEdge.node;
        
        if (!visited.contains(node)) {
            visited.add(node);
            backpointers.put(node, nodeEdge.edge);
            if (node == goal) {
                return reconstructPath(start, goal, backpointers);
            }
            for (Edge edge : node.edges) {
                Node neighbour = edge.neighbour;
                if (!visited.contains(neighbour)) {
                    int lengthToNeighbour = nodeEdge.length + edge.length;
                    fringe.add(new NodeEdge(neighbour, edge, lengthToNeighbour));
                }
            }
        }
    }
    return null;
}

private List<Node> reconstructPath(Node start, Node goal, Map<Node, Edge> backpointers) {
    List<Node> path = new ArrayList<>();
    Node current = goal;
    while (current != start) {
        path.add(current);
        current = backpointers.get(current).start;
    }
    path.add(start);
    Collections.reverse(path);
    return path;
}

private class NodeEdge implements Comparable<NodeEdge> {
    public Node node;
    public Edge edge;
    public int length;

    public NodeEdge(Node node, Edge edge, int length) {
        this.node = node;
        this.edge = edge;
        this.length = length;
    }

    @Override
    public int compareTo(NodeEdge other) {
        return Integer.compare(length, other.length);
    }
} 

```
