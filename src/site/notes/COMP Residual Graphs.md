---
{"dg-publish":true,"permalink":"/comp-residual-graphs/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 30-04-2023
***

# Residual Graphs

Given a network $G$ and a flow $f$, we construct a residual graph $G_f$

$G_f$ is defined as:
- $G_f$ contains same nodes as $G$
- Forward edges
	- for each edge $e=(u,v)$ of $G$ 
	- for which $f_e < c_e$ include an edge $e' = (u,v)$ in $G_f$
	- with capacity $c_e - f_e$
- Backward edges (represent decreasing flow)
	- each edge $e = (u,v)$ with $f_e > 0$
	- include an edge $e' = (v,u)$ in $G_f$ with capacity $f_e$

# Augmentation Path

Any flow $g$ on residual graph $G_f$ from source $s$ to destination $t$

- Graph consisting of forward edges and backward edges

Path $g$ can be added to $f$ to get a new flow on $G$
- $g_e$ (forward edge) adds to $f_e$
- $g'_e$ (backwards edge) subtracts from $f_e$ 
	- Equivalent of reversing our previous decision





