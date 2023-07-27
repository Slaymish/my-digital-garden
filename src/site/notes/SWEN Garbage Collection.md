---
{"dg-publish":true,"permalink":"/swen-garbage-collection/"}
---

Related: [[Garbage Collection\|Garbage Collection]] [[Memory Leaks\|Memory Leaks]] #java #programming  
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-03-2023
***

# Java Memory Model

- Compared to C++/C, where can manually alloc/dealloc [^1]
- Object memory address can't be accessed by programmer
- Memory address **can** be changed during object lifetime

## Updates to come

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

### How to Handle an OutOfMemory exception

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


***

# JVM Tuning

- Can locally change options
-  Memory management etc


- Can attempt to force Garbage Collection:

```java
System.gc(); // requests it, can fail
```

## WeakReferences

- Java class: `WeakReference` is a part of the `java.lang.ref` package used to create weak references to objects.
- Memory management: It enables more efficient garbage collection by allowing the JVM to collect objects when they're no longer in use.
- Use case: Ideal for creating caches, as it enables the garbage collector to reclaim memory resources once the object is no longer needed.
- Behavior: When a `WeakReference` is the only reference to an object, it is eligible to be garbage collected.
- Creation: To create a `WeakReference`, use the constructor `WeakReference<T>(T referent)`, where `T` is the object's type.
- Accessing: `.get()` method is used to access the referent. If the referent has been garbage collected, this method returns `null`.
- Clearing: Use `.clear()` to explicitly clear the reference, making the referent eligible for garbage collection.


Next: Generics

[^1]: [[NWEN241/NWEN Dynamic Memory Management\|NWEN Dynamic Memory Management]]
[^2]: [[NWEN241/NWEN Storage Classes#^c0dd0a\|Same as C heap]]