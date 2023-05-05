---
{"dg-publish":true,"permalink":"/page-rank/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 05-05-2023
***

# Page Rank

- Measure the *transitive influence* of nodes (influence of neighbours and neighbours of neighbours of neighbours)

## Introduction to Page Rank Algorithm

A page with more high-quality links pointing to it should be ranked higher than a page with fewer or lower-quality links.


Here are the basic steps of the algorithm:

1. Create a matrix representing the internet's link structure, where each cell represents an edge between two nodes (web pages). If there's a link from page A to page B, set the value at row A and column B in the matrix to 1, otherwise 0.

2. Normalise each row in the matrix so that its elements sum up to 1. This creates a stochastic matrix representing probabilities of transitioning from one page to another.

3. Choose an initial Page Rank vector (usually assigning equal probability to all nodes) and iteratively multiply this vector by the stochastic matrix until convergence is reached (i.e., when changes between iterations become very small).

4. The resulting converged vector will contain values representing relative importance scores for each node.

# Terminology

- Back-edge
	- if page A links out to page B, then page B is said to have a 'backlink' from page A

- $PR(P)$ - Each page $P$ has a notion of its own page rank

- $C(P)$ - Count of outgoing links for page $P$. Each Page spreads its vote out evenly amongst all of it's outgoing links

![200][SCR-20230505-qgv.png]

Page rank of $P$ is dependent on the page rank of the pages that have an outgoing link to $P$ (nodes pointing to $P$)[^1]

The Page rank transferred from a given page to the target of its outgoing links is divided equally among all outbound links[^2]

[^1]: EG: Page rank of A depends upon page ranks of C and D
[^2]: EG: If the page rank of C is .2, both the page rank transferred to both A and B will be .2/2 = .1