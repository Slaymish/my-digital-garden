---
{"dg-publish":true,"permalink":"/comp-assignment-3-marking-prep/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-06-2023
***

# Marking Prep

## Edmond Karp

## Page Rank

Definition: Measures the **importance** of each page based on the quantity and quality of links to a page.

- Initialisation: All nodes start with equal rank.
- Iteration: Update each city's rank based on the ranks of its neighbours.
- Damping Factor: Lessens the impact of links from cities with many outbound links (set to 0.85 in your code).

### Compute Influence

- Finds most influential node **for city**
- The node that, when removed, will cause the largest drop in PageRank for the specified city

### calculateHypotheticalRank

- Calculates potential pankrank on given city with one city excluded



