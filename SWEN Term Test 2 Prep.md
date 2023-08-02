---
dg-home: false
dg-publish: true
---
Related: #
Contents: [[SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 24-04-2023
***

Similar to [[SWEN Term Test Prep\|term test 1]]

# Term Test 2

*Friday 28th April*

- Tutor helpdesk **Thursday 12-2pm** in CO219

- Questions divided into parts (same as lab)

- Will get resource with test (ss's on screenshots)

## Prep Info

- [ ] Do lab 5 questions again
- [ ] Make own practise qs





**For loop: continues if the two values are the same**
`if(f.city().equals(city){ continue; }`

# Examples

```java
return fs.stream()
	.filter(f -> f.city().equals(city))
	.max(Comparator.comparing(Flower::height))
	.orElseThrow(IllegalArgumentException::new);
```

or 

```java
return fs.stream()
	.filter(f -> f.city().equals(city))
	.reduce()
	.orElseThrow(IllegalArgumentException::new);
```

## .filter()

- Used on a stream of objects to filter and keep only those elements that meet the specified condition.

## Compact Constructor

*Will be in term test*

```java
Kangaroos{
	assert x;
	assert y;
	assert z;
}
```

- Recursion

# To Iterate a Map

- Methods
	- .entrySet()
	- .getKey()
	- .getValue()
- Use stream on .entrySet()

```java
return ps.entrySet().stream()
	.min(Comparator.comparing(e->e.getValue().distance(target)))
	.map(e->e.getKey()) // Map on optional here
	.orElseThrow(IllegalArgumentException::new);
```