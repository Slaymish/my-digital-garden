---
{"dg-publish":true,"permalink":"/graph-of-thought-go-t/"}
---

Related: #AI
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-06-2023
***

# Graph of Thought (GoT)

- [[GoT Paper\|GoT Paper]] based on these notes

- An extension to the Tree-of-Thought LLM processing idea[^1]

- A way for the conversation to be represented in a graph-like manner

## Implementation Idea

- Have measure each prompt by its vector similarity
- Then construct edges between the most similar
- Could set a threshold variable to change how many edges are added
- Would also store a list of the sequential order as well
	- Could maybe factor the order into how the edges are constructed

### Algorithms

1.  [[COMP Graph Analytics\|COMP Graph Analytics]]
	1. [[Closeness centrality\|Closeness centrality]]
	2. [[Degree centrality\|Degree centrality]]
	3. [[Between centrality\|Between centrality]]
	4. [[Page Rank\|Page Rank]]
2. [[A* Algorithm\|A* Algorithm]]
	- Could base the heuristic on some weight decided on something
		- Maybe vector similarity between the users prompt?
1. [[Djikstra's Algorithm\|Djikstra's Algorithm]]

[^1]: A good example of this can be found here <https://github.com/kyegomez/tree-of-thoughts>