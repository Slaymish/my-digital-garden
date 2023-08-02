---
dg-home: false
dg-publish: true
---
Related: #programming #java #graphs 
Contents: [[COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 11-05-2023
***

# Kruskal's Algorithm

- Results in a minimum [[Spanning Trees]]

## Steps

- Look for **smallest edge** in edge list
- If it doesn't cause a [[Cycles\|cycle]], add edge
- Keep going until all nodes in same tree

## Time Complexity

- Where E is the number of edges

$$O(Elog(E))$$

### Pseudocode

```
function Kruskal(G):
    F = new forest with vertices of G
    S = edges of G sorted by weight
    while S is not empty:
        take smallest edge e from S
        if e connects two different trees in F:
            add e to F
        else:
            discard e
    return F
```

## Example Code

```java
    public SpanningTree Kruskals() {
        PriorityQueue<Edge> queue = new PriorityQueue<>(Comparator.comparing(Edge::getWeight));
        queue.addAll(Arrays.asList(edges));

        DisjointSet<Vertex> forest = new DisjointSet<>();
        for (Vertex vertex : vertices) {
            forest.makeSet(vertex);
        }

        SpanningTree tree = new SpanningTree();
        while (!queue.isEmpty()) {
            Edge edge = queue.poll(); // Get the edge with the smallest weight
            Vertex root1 = forest.findSet(edge.getVertex1());
            Vertex root2 = forest.findSet(edge.getVertex2());

            // If the edge connects two different trees, add it to the tree
            if (root1 != root2) {
                tree.addEdge(edge);
                forest.union(edge.getVertex1(), edge.getVertex2());
            }
        }

        return tree;
    }
}
```
