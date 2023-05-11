---
{"dg-publish":true,"permalink":"/comp-test-3-prep/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 11-05-2023
***

# Test 3

- Everything from week 7 - week 9 (Tuesday week 9)
- No lecture today

## Example Questions

### Network Flows

- Constraints on a network flow graph
	- [[Capacity constraint\|Capacity constraint]]
	- [[Balance constraint\|Balance constraint]]

- Given a graph follow steps of [[Edmond-Karp algorithm\|Edmond-Karp algorithm]] (Pseudo-code provided in test)
	- Find augmentation paths and the associated flow
	- At a given step, what will be the contents of a different data structure?
		- [[COMP Residual Graphs\|COMP Residual Graphs]]
		- Map of back-pointers

- Write java code to accomplish a given task

### Centrality

- Given a scenario, which of the different [[COMP Monopoly and Oligopoly#Centrality Algorithms\|centrality algorithms]] will be the most useful and why?

- Given a scenario, compare the use of different centrality measures

- Show steps of [[Page Rank\|Page Rank]] on a given graph (Pseudo code given)

### Cycles and Spanning Trees

- Given a *static graph*, run [[Depth-First traversal\|Depth-First traversal]] to detect possible cycles (Pseudo code provided)

- Given a *dynamic graph* with edges joining one after the other, detect is adding a new edge will create a cycle

- Given a graph, find minimum cost [[Spanning Trees\|spanning tree]] using [[Prim's algorithm\|Prim's algorithm]]/[[Kruskal's Algorithm\|Kruskal's Algorithm]]

### General

- Given a scenario that can be modelled using graphs, which category of graph problems would it belong to:
	- [[COMP Graph Analytics#Graph Query\|Graph Query]]
	- [[COMP Graph Analytics#Graph Algorithm\|Graph Algorithm]]
	- [[COMP Graph Analytics#Graph Analytics\|Graph Analytics]]

- Analytical questions
	- Why we need a given step in the algorithm
		- [[Edmond-Karp algorithm\|Edmond-Karp algorithm]]
		- [[Page Rank\|Page Rank]]
		- [[Prim's algorithm\|Prim's algorithm]]
		- [[Kruskal's Algorithm\|Kruskal's Algorithm]]
	- What if we modify the algorithm in a given way?
	- What if we had a specific **type of** graph as input


***

# Notes

- [[COMP Ford-Fulkerson method\|COMP Ford-Fulkerson method]]
	- Can only choose paths with
		- Non-full forward edges
		- Non-empty backwards edges
- [[Kruskal's Algorithm\|Kruskal's Algorithm]]
	- Find smallest edge (A,F)
	- If doesnt cause a cycle, add to list
	- repeat until all nodes in same tree


