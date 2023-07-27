---
{"dg-publish":true,"permalink":"/updating-residual-graph/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 11-05-2023
***

# Updating Residual Graph

```
For each edge in the augmentation path
	- Increase  flow by bottle neck
	- Decrease capacity by bottleneck
	- Increase capcity in the reverse edge by bottleneck
```