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

### Example problems
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


## Definition
- For connected, **directed** graph $G=(V,E)$
- Each edge, $e$, has a non-negative int capacity $c_e$
- One (or more) vertex is labelled as a source $s \epsilon V$
- One (or more) vertex is labelled as sin $t \epsilon V$
- No edges enters the source and no edge leaves the sink

![300][SCR-20230427-gj7.png]


### Flow in a flow network

- Each edge has a total flow, $f_e$
- $f_e =$ amount of material carried on the edges $e$
- $f_e$ is not the same as capacity


### Constraints
- Capacity constraint
	- Flow can never exceed the capacity
- Balance constraint
	- Can't bottle neck
	- Whatever comes in, must go out


