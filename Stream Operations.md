---
dg-home: false
dg-publish: true
---
Related: #
Contents: [[SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 30-05-2023
***

[[SWEN Stream]]
[[Java Streams]]

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

