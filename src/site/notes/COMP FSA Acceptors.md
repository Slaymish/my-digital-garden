---
{"dg-home":false,"dg-publish":true,"permalink":"/comp-fsa-acceptors/","dgPassFrontmatter":true}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 25-03-2023
***


# Finite State Automata
- 'FSA'
- Represents computation process
- Finite number of states
- Input alphabet defines transitions
- One initial state
- Zero or more final states
- Accepts or rejects input strings
- Used in pattern matching, compilers, and control systems


<h1 align="center">
Regular Expressions = A FSA
</h1>


## FSA Acceptors
- Label on edges correspond to input values
- Start state and end state(s)
- If end up in an end state with no more input, then fsa accepts the input
- Deterministic
![250][SCR-20230325-ocl.png]

- Non-deterministic
	- Two branches from a state have the same label
	- Have to make a choice/may have to backtrack
	- Can always turn a non-deterministic FSA to a deterministic one



## Simple matching algorithm:
```java
state = startState
while (state is not endState & text has a next char){
	nextState = lookup(state,nextChar);
	if(nextState=-1)return false
	state = nextState
}
if(state is an endState)return true
else return false
```
- Works for a *deterministic* FSA