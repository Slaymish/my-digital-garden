# Adjacency List

## Representing in java

```java
int[][] graph;
An adjacency list is a representation of a graph where each vertex has a list of its neighboring vertices. In Java, this can be represented using arrays, lists, or maps.

Here's an example using a 2D array:

```java
// Example graph:
// 0 -- 1 -- 2
// |         |
// +---- 3----+

int[][] graph = {
    {1, 3}, // Neighbors of vertex 0
    {0, 2}, // Neighbors of vertex 1
    {1, 3}, // Neighbors of vertex 2
    {0, 2} // Neighbors of vertex 3
};
```

Alternatively, you can represent the graph using an ArrayList:

```java
import java.util.ArrayList;

// Example graph:
// 0 -- 1 -- 2
// |         |
// +----3 ----+

ArrayList<ArrayList<Integer>> graph = new ArrayList<>();

graph.add(new ArrayList<>()); // Vertex:0 -> Neighbors: [1,3]
graph.get(0).add(1);
graph.get(0).add(3);

graph.add(new ArrayList<>()); // Vertex:1 -> Neighbors: [0,2]

```