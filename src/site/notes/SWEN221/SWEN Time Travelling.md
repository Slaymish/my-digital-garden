---
{"dg-publish":true,"permalink":"/swen-221/swen-time-travelling/"}
---

Related: #java 
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 07-03-2023
***
Static type:
- The type of a value as seen by the compiler

Dynamic type:
- The type of a value at runtime

```java
class Horse implements Animal {
	..
	public double speed(){
		return 10d;
	}
	..
}

interface Animal {
	..
	default void run(Point2d dest){
		double s = this.speed();	
		..
	}
}
```

```java
Animal x = new Horse(...);
x.run(myDest);
```
- Above is an example of **time travelling**
- Animal.run is calling Horse.speed
- Which existed *after* animal


## Time travelling:
### Pros:
- Future users of your code can, make better use/reuse your code
- Enables better testing and mock objects
### Cons:
- Open code
	- Can overide vars
- Design for dynamic dispatch to prevent


### To stop time travelling:
- use the 'final' keyword
- A final class cannot be extended
- A final method can not be overriden
- *Records are final by default*

