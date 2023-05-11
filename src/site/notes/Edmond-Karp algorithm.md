---
{"dg-publish":true,"permalink":"/edmond-karp-algorithm/"}
---


Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 05-05-2023
***

# Edmond-Karp Algorithm

The Edmond-Karp algorithm is an improvement on the classic Ford-Fulkerson algorithm for computing the maximum flow in a flow network. It is named after Yefim Dinitz (also known as Edmonds) and Jack Edmondson (also known as Karp), who independently discovered this algorithm in 1972.

## Overview

The Edmond-Karp algorithm is an implementation of the Ford-Fulkerson method that uses the shortest augmenting path rule, which means that it always selects the shortest path (in terms of the number of edges) that can still be augmented with available capacity. This choice leads to a better runtime complexity compared to the original Ford-Fulkerson algorithm.

The Edmond-Karp algorithm is used to find the maximum flow in a flow network, which is a directed graph where each edge has a capacity and a flow value. The goal is to maximize the total amount of flow from a source node to a sink node while respecting the capacities of each edge.

## Algorithm Steps

1. Start with an initial flow of zero for all edges in the network.
2. While there exists an augmenting path from source to sink:
   1. Find the shortest augmenting path using Breadth-First Search (BFS), considering only edges with available capacity.
   2. Determine the minimum residual capacity along this path.
   3. Update the flow along this path by adding/subtracting (depending on direction) this minimum residual capacity.
3. The maximum flow is reached when no more augmenting paths can be found.

## Complexity

The time complexity of the Edmond-Karp algorithm is $O(V * E^2)$, where V represents the number of vertices and E represents the number of edges in the network. This improvement over [[COMP Ford-Fulkerson method\|COMP Ford-Fulkerson method]] method, which has no specific time complexity guarantee, makes Edmond-Karp more suitable for larger networks.

## Peusdo Code

```
EdmondKarp(G,s,t){
	Let f(e) = 0 for all edges (no flow anywhere)
	Initalize residual graph RG 
		// for every forward edge in G, add a reverse edge
		// with a capacity 0

	int maxFlow = 0;
	Repeat
		Use BFS to find a path P path from s to t
}
```
