---
{"dg-publish":true,"permalink":"/lecture-notes-swen/"}
---


Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
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

abstract Mob.dropSkull()



```

