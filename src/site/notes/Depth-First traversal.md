---
{"dg-publish":true,"permalink":"/depth-first-traversal/"}
---


# Depth-First Traversal

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-03-2023
***

# Recursive DFS

- Works on undirected *and* directed graphs

## Example Pseudo-code

```
TraverseGraph(node)
	if node is not visited:
		visit the node
		process the node
		for each neighbor of node:
			if neighbour is not visited:
				TraverseGraph(neighbour)

```

### Recording Visited:

- Mark the node (not a good option)
- Keep a set of visited nodes (good option)

***

Depth-first traversal in Java refers to a way of traversing a tree or graph data structure that starts at the root node and explores as far as possible along each branch before backtracking. This can be achieved using recursion or a stack data structure.

Here are some notes on how to implement depth-first traversal in Java:

1. Define a node class that represents the elements of the tree or graph structure. This node class should have fields for storing the node value, a list of its children (for trees) or neighbors (for graphs), and a boolean flag indicating whether the node has been visited or not.

2. Define a method for performing the depth-first traversal. This method should take the root node as an argument and return a list of nodes visited during the traversal.

3. Within the depth-first traversal method, mark the current node as visited and add it to the list of visited nodes.

4. Loop through the children or neighbors of the current node and recursively call the depth-first traversal method on each child or neighbor that has not been visited.

5. After exploring all the children or neighbors of the current node, backtrack to the parent node and repeat the process on any unvisited neighbors.

6. Repeat steps 3-5 until all nodes in the tree or graph have been visited.

Here's some sample code to perform a depth-first traversal using recursion:

```java
public List<Node> depthFirstTraversal(Node root) {
    List<Node> visited = new ArrayList<>();
    if (root != null) {
        depthFirstTraversalHelper(root, visited);
    }
    return visited;
}

private void depthFirstTraversalHelper(Node current, List<Node> visited) {
    visited.add(current);
    current.setVisited(true);
    for (Node neighbor : current.getNeighbors()) {
        if (!neighbor.isVisited()) {
            depthFirstTraversalHelper(neighbor, visited);
        }
    }
}
```

Note that this is just one way of performing depth-first traversal in Java, and there are other variations that use iterative approaches or customized data structures.
