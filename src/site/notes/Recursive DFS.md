---
{"dg-publish":true,"permalink":"/recursive-dfs/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-04-2023
***
[[COMP Graphs and data structures\|COMP Graphs and data structures]]

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



### Recording visited:
- Mark the node (not a good option)
- Keep a set of visited nodes (good option)