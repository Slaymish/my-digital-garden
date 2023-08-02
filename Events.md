---
dg-home: false
dg-publish: true
---
Related: [[SWEN221 MOC]]
Contents: [[SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC]]
Hamish Burke || 27-07-2023
***

# Events

Used in [[UML State Diagrams]]

## Kinds of Events

- SignalEvent
	- Asynchronous event
	- Is queued by the receiver until its ready to handle
- CallEvent
	- Synchronous message by an object
	- invoking a call of an operation
- TimeEvent
	- *After* a specified time, does event