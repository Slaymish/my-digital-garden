---
{"dg-home":false,"dg-publish":true,"permalink":"/swen-garbage-collection/","dgPassFrontmatter":true}
---

Related: [[Garbage Collection\|Garbage Collection]] [[Memory Leaks\|Memory Leaks]] #java #programming  
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-03-2023
***

# Java Memory Model
- Compared to C++/C, where can manually alloc/dealloc [^1]
- Object memory address can't be accessed by programmer
- Memory address **can** be changed during object lifetime


### Updates to come
- [[Valhalla\|Valhalla]]
	- Combines primitive types and objects
- [[Lilliput\|Lilliput]]
	- Less memory for each object


***

# Objects and Memory
- All objects created on the heap [^2]

## Reachable Object
- If a reference is stored in a local var or static field
- Or stored in a field or array of a reachable object


### How to handle an OutOfMemory exception
- Catch the exception
- From beginning, declare static array of ints
	- Size is amount you memory you need
- Use that reserved space


***

# Mark 'n Sweep
*Method of garbage collection*

- Reachable objects are marked
	- Traversing form objects 'roots'
	- Could use something like [[Depth-First traversal\|depth first traversal]] 
- Marked object are 'swept' to the left
- Reclaim unmarked objects



[^1]: [[NWEN241/NWEN Dynamic Memory Management\|NWEN Dynamic Memory Management]]
[^2]: [[NWEN241/NWEN Storage Classes#^c0dd0a\|Same as C heap]]
