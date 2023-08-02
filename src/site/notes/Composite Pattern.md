---
{"dg-publish":true,"permalink":"/composite-pattern/"}
---

Related: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
Contents: [[SWEN225 MOC\|SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-08-2023
***

# Composite Pattern

## When to Use

- Want to represent **part-whole hierarchies** of objects
- Client should not be aware of wether dealing with individual or composed objects

![250][SCR-20230802-mult.png]

**Participants**
- Component
	- Declares interface
- Leaf
	- Concrete classes
- Composite
	- Aggregates children
- Client
	- Only aware of Component ([[Polymorphism\|Polymorphism]] is maintained)

**Consequences**
- Primitives can be recursively composed
- New components can be easily added
- Clients treat composite and primitives uniformly

# Implementation

- Client can only add components to groups (not primitives)
	- So may need to distinguish between the two
	- Whether to add all group operations to Component or not
		- Or only have available to Composite
	- Could have add/remove(component) have a default impl of throwing an exception
		- This means it'd work for primitives (even in Component class)




***

## Example

Children of *Group* can be line/text **or** another *Group*

![300][SCR-20230802-mtke-2.png]
