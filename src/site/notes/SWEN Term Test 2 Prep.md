---
{"dg-publish":true,"permalink":"/swen-term-test-2-prep/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-04-2023
***

Similar to [[SWEN221/SWEN Term Test Prep\|term test 1]]

# Term test 2
*Friday 28th April*

- Tutor helpdesk **Thursday 12-2pm** in CO219

- Questions divided into parts (same as lab)

- Will get resource with test (ss's on screenshots)



### Prep info
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

### .filter()
- Used on a stream of objects to filter and keep only those elements that meet the specified condition.


### Compact constructor
*Will be in term test*

```java
Kangaroos{
	assert x;
	assert y;
	assert z;
}
```


- Recursion
