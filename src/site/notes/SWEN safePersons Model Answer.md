---
{"dg-publish":true,"permalink":"/swen-safe-persons-model-answer/"}
---


Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 10-05-2023

***

# SWEN safePersons Model Answer

```java 
static list<Person> safePersons(Map<Point,List<Person>> ps, LIst<Point> dl){
	// with entry set
	ps.entrySet().stream()
		.filer(e -> !dl.contains(e.getKey()))
		.flatMap(e -> e.getValue().stream()) // returns stream of people
		.toList();


	// with key set
	ps.keySet().stream()
		.filter(e -> !dl.contains(e))
		.flatMap(e - > ps.get(e).stream()) // 
		.toList();

	// with mapMulti
	ps.entrySet()
		.stream()
		.filter(e -> !dl.contains(e.getKey()))
		.<Person>mapMulti((entry,con)->{
			entry.getValue().stream().forEach(con::accept);
		})
		.toList();
}
```

## Iterate Map

- Can do entrySet or keySet

### Flat Map

*Non terminal operation*

#### Stream.flatmap

```java
Stream.flatMap e -> Stream<E> // returns stream
```

#### optional.flatmap

```java
Optional.flatMap e -> Optional<E> // returns optional containing e
```