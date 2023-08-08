---
{"dg-publish":true,"permalink":"/data-flow-diagrams/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Data Flow Diagram

## Trust Boundaries

- Everywhere two (or more) principals interact
- All *interesting* boundaries are semi-permeable
	- Air gaps
	- Firewalls
	- Require policy mechanisms (which are hard)
- Formal methods help build boundaries
	- Isolation
	- Type safety
	- Policy languages
	- Reference monitors/kernels

## Example

![Pasted image 20230727102553.png](/img/user/Pasted%20image%2020230727102553.png)

## Data Flow Diagram

### Rules

1. Dataflow cannot happen between two entities
2. Data cannot flow between two datastores
3. Cannot flow directly from an entity to data store
4. Must have at least one input data flow and one output dataflow
	- When you have a process, something must come out/in
5. A data store must have at least one input data flow and one output data flow
6. Two data flows can not cross each other and all processes must be linked to minimum none data store or any other process


