---
{"dg-publish":true,"permalink":"/comp-assignment-3-info/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-05-2023
***

# Assignment 3 Info

## Files to Submit

- EdmondKarp.java [[Edmond-Karp algorithm\|Edmond-Karp algorithm]]
- PageRank.java [[Page Rank\|Page Rank]]

## Why Use a String for the Node Id's?

- Maintain consistency
- Its string everywhere else
- Avoid you having to do typecasting

## Building a Residual Graph:

- **Duplicate** edges from initial graph
	- Don't have to update original graph at all
- In EdmondKarp.java, do computeResidualGraph()
- ArrayList of edges[^1]
	- Each has index value
- At each step, add an edge
- Forward edges = original edges of graph
- for every **node** have a collection of edge ids that associated with it

- Even indexes store forwards edges
- Odd indexed store reverse edges

## Network Flow

- Once residual graph built
- Implement calcMaxFlows()
	- Invoke BSF method (edmond-karp because doing [[COMP Ford-Fulkerson method\|ford-fulkerson]] with bfs)
		- Returns Path *and* bottleneck
- backpointer will consistence of nodes

## Page Rank

- implement computeLink()
	- updates fromLink and toLink in city class
- implement computePageRank() from slides
	- use iter and dampingfactor defined at top
	- create map of nodes `Map<Rank,node>`

[^1]: for assignment, using `Map<String,Edge> edges;`