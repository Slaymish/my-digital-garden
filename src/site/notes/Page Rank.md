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

# Terminology

- Back-edge
	- if page A links out to page B, then page B is said to have a 'backlink' from page A

- $PR(P)$ - Each page $P$ has a notion of its own page rank

- $C(P)$ - Count of outgoing links for page $P$. Each Page spreads its vote out evenly amongst all of it's outgoing links

![200][SCR-20230505-qgv.png]

Page rank of $P$ is dependent on the page rank of the pages that have an outgoing link to $P$ (nodes pointing to $P$)[^1]

The Page rank transferred from a given page to the target of its outgoing links is divided equally among all outbound links[^2]

## Random Surfer Model

- The PageRank theory holds that an imaginary surfer who is randomly clicking on links will eventually stop clicking

## Damping Factor

- The probability, at any step, that the person will continue following links is a damping factor $d$. The probability that they instead jump to any random page is $1-d$


$$PR(A) = (1-d) + d \sum \frac {PR(inLinkNeighbour)}{count(outbound links of inLinkNeighbour)}$$

***

# Example

$PR(A) = PR(B) = PR(C) = PR(D) = 1/4$
$d=0.85$

Iter 1:
$$PR(A) = 0.15 + 0.85*(\frac {PR(B)}{2} + \frac {PR(D)}{3})$$


$$PR(B)= 0.15 + 0.85*(\frac {PR(A)}{3} + \frac {PR(C)}{1} + \frac {PR(D)}{3})$$

***

# Page Rank Pseudocode

- get num of nodes

- for each node, set the page rank to 1/num of nodes
- repeat for iter
	- for each node in graph
		- set nRank = 0
		- for each back-edge of node
			- 

```java
computePageRank(Graph graph, int iter, double dambing factor){
	nNodes = graph.getNodeAmount();
	// initalise
	for(Node node: graph.getNodes()){
		node.setPageRank(1/nNodes);
	}
	
	int count = 1;
	while(count<inter){
		for(Node node: graph.getNode()){
			int nRank = 0;
			for(Node neighbour:node.getbackNeighbours()){
				neighbourShare = pageRank(backneighbour)
				/neighbour.outEdgeNum();
				
				nRank = nRank + neighbourShare
			}
			nRank = (1 - dampingFactor)
			+ dampingFactor*nRank;
			
			pageRank(node) = nRank
		}
		count++;
	}
}
```

[^1]: EG: Page rank of A depends upon page ranks of C and D
[^2]: EG: If the page rank of C is .2, both the page rank transferred to both A and B will be .2/2 = .1