---
dg-home: false
dg-publish: true
---

Related: #
Contents: [[SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 08-05-2023
***

# Minecraft Bug

```
Skeleton.die:
	if(skeleton is normal){
		drop normal skull;
	}
	else{
		drop wither skull;
	}
```

- When new type of skeleton was added, it dropped a wither skull instead

## Why If's Are Bad?

- Code remains hidden
- Expanding code in the future, if's remain the same

## Correct way

```java
Mob.die:
	when killed by charged creeper:
		this.dropSkull()

abstract Mob.dropSkull() // to be overriden

//-------//

NormalSkeleton.dropSkull():
	drop(skeleton_skull)
	
WitherSkeleton.dropSkull():
	drop(wither_skull)

StraySkeleton.dropSkull():
	drop(stray_skull)



```

### When to If?

- When a choice is **binary**
	- Point inside or outside a bounding box
	- Elements inside/outside list
	- List empty/not
- When working with legacy code/ methods returning booleans

### When **not** to if

- Because you have no idea how else to code
- *When set of options may change over time*
- When **response** to an option may change, or want it customisable by user
w