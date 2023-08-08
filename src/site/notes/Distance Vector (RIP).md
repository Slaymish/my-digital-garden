---
{"dg-publish":true,"permalink":"/distance-vector-rip/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 31-07-2023
***

# RIP

<https://book.systemsapproach.org/internetworking/routing.html#distance-vector-rip>

- Aak **Bellman-Ford**
- Each [[Local Area Networks\|Local Area Networks]] is one node in a graph

- Each node keeps a **vector of distances** to every other node
- Algorithm **settles/converges** to the best solution
- **Unstable**, can cause link failures if stuff goes down
	- Which is why [[OSPF\|OSPF]] is used now

1. Starts with initial **routing table**

Similar to [[Forwarding Table\|Forwarding Table]], but for routes

## Periodic Update

- serves to let other nodes know this node still exists

## Triggered Update

- occurs whenever a node notices a *link failure*

## Example of Algorithm

### For A

| Dest | Cost | Next-hop |
| ---- | ---- | -------- |
| B    | 3    | B        |
| F    | 6    | F        |
| E    | 1    | E        |
| C    | ∞    | -        |
| D    | ∞    | -        |

### For B

| Dest | Cost | Next-hop |
| ---- | ---- | -------- |
| A    | 3    | A        |
| E    | 1    | E        |
| C    | 4    | C        |
| D    | ∞    | -        |
| F    | ∞    | -        |

2. Each *iteration*

Each time you find a better route, update the values in the routing table

### For A

| Dest | Cost | Next-hop |
| ---- | ---- | -------- |
| B    | 3    | B        |
| F    | 6    | F        |
| E    | 1    | E        |
| C    | **7**    | **B**        |
| D    | ∞    | -        |
