---
{"dg-publish":true,"permalink":"/comp-flow-network/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-04-2023
***

# Flow Network

## Example Problems

- Road Network - Flow of vehicles
	- How *fast* can I evacuate a city in emergency
- Distribution network - Network of pipelines
	- Whats the *max amount* the can be transferred from A-B
- Computer network - Flow of packets
	- What *rate* can I transfer data from A-B


In network flow problems:
- Edges have max capacities
- Source node generates traffic
- Sink nodes absorb traffic as it arrives
- Traffic is transmitted across the edges


<p align="center">
Calculate the flow of a path by taking the minimum capacity of it
</p>

# Definition

- For connected, **directed** graph $G=(V,E)$
- Each edge, $e$, has a non-negative int capacity $c_e$
- One (or more) vertex is labelled as a source $s \epsilon V$
- One (or more) vertex is labelled as sin $t \epsilon V$
- No edges enters the source and no edge leaves the sink

![300][SCR-20230427-gj7.png]

## Flow in a Flow Network

- Each edge has a total flow, $f_e$
- $f_e =$ amount of material carried on the edges $e$
- $f_e$ is not the same as capacity

## Constraints

- Capacity constraint
	- Flow can never exceed the capacity
- Balance constraint
	- Can't bottle neck
	- Whatever comes in, must go out


***

# Example

- find all paths
	- Can use [[Breath-first traversal\|Breath-first traversal]]
	- Has some issues
- find the minimum capacity edge for each path
- that's the flow for that path
- add all them together to get total flow

On edges with flow and capacity 20, write as $20/20$ where $f_e/C_e$

To every edge in a flow, try to add a [[COMP Flow Network#Reverse Edges\|reverse edge]]


***

# Reverse Edges

*Reverse edges allow us to reverse our decisions*

- Use [[Breath-first traversal\|Breath-first traversal]] to find shortest edge
- Every time you add a flow, set the capacity of the reverse edge to reflect the flow gathered
- **Reverse edges cancel the flow**

![400][SCR-20230430-t0i.png]




All of above is the [[COMP Ford-Fulkerson method\|Ford-Fulkerson method]]

