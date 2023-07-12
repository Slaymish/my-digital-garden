---
{"dg-publish":true,"permalink":"/comp-graph-analytics/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-04-2023
***

# Graph Analytics

*Three levels*

## Graph Query

- Attempt to identify an explicit pattern with the graph 
- Usually they find a *known subset* of the important nodes in the graph
	- Eg Find me all friends Dan and Kevin share
	- Finds
		- Set of friends of Dan
		- Set of friends of Kevin
		- Intersection of two sets

## Graph Algorithm

- In addition to selecting/grouping nodes,
- Also involves categorising them or some other processing to sort them or learn something from them
- Eg
	- Find me the shortest path between Dan and Kevin
	- Finds
	- Of all the paths between Dan and Kevin, the shortest
- A query helps you find things you knew you where looking for
- An algorithm can tell you what nodes are most interesting

## Graph Analytics

- Tells us something about the graph in general
- Nearly all nodes will be inspected as a part of the calculation
- Eg
	- Who are the most influential nodes in the network
	- Finds
		- Of all the nodes in the network, nodes with the highest number of followers


***

### Path Finding

-  Shortest path from A-B
- Average shortest path
- Longest path
- Minimum spanning tree
- The max flow that can take place between two nodes in a transportation network
	-  [[COMP Flow Network\|COMP Flow Network]]

### Centrality

- Finding which nodes are more important in a network
	- eg Articulation points

### Community Detection

- Identifying common attributes
- eg hubs/hierarchies/tendencies


