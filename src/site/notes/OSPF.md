---
{"dg-publish":true,"permalink":"/ospf/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-08-2023
***

# Link State Routing

- aka [[Djikstra's Algorithm\|Djikstra's Algorithm]]
- To be used for [[Routing\|Routing]] instead of [[Distance Vector (RIP)\|Distance Vector (RIP)]]
- Idea is so every node can create a **complete map** of the network

Each node creates an **update packet**, called a [[link-state packet (LSP)\|link-state packet (LSP)]]

## Route Calculation

- not in exam 

Based on [[Djikstra's Algorithm\|Djikstra's Algorithm]] forward search
Each node maintains two lists, **Tentative** and **Confirmed**

- Each list contains entries in the form:

```
(Desination, Cost, NextHop)
```

1. Init Confirmed list with an entry for myself
2. For ....

- If Tentitive list becomes empty, we are done

## For Example

Then:

![300][SCR-20230803-mmng-2.png]

1. LSP arrives at node X
2. X floods LSP to A and C
3. A/C flood LSP to B (but not each)
4. Flooding complete

### Challenges

- Does not scale to the internet
- The '[[autonomous systems\|autonomous systems]]' may not want to route your packets

## Routing Areas

- To address the scalability of [[OSPF\|OSPF]]

Partition a routing domain into subdomains
Called **Routing Areas**

- Only flood the routing areas
- Only compute shortest path to other nodes in your area




