---
{"dg-publish":true,"permalink":"/stream-operations/"}
---

Related: #
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 30-05-2023
***

[[SWEN Stream\|SWEN Stream]]
[[Java Streams\|Java Streams]]

```
/** Non terminal operations (returns stream)
 * filter()
 * map()
 * flatMap()
 * distinct()
 * limit()
*/

/** Terminal operations
 * .toList()
 * collect()
 * count() // returns int of number of elems in stream
 * max()
 * min()
 * forEach() // perform an op on each elem in stream
 * toArray()
*/
```

# distinct() (removes duplicates)

- find unique objects in collection

```java
vehicleList.stream()
	.distinct() // acts as adding to set (removes duplicates)
	.toList();
```

