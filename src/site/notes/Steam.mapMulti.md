---
{"dg-publish":true,"permalink":"/steam-map-multi/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

<h1 align="center">
Stream.mapMulti
</h1>

- Allows use of [[Types of Programming#Imperative Programming\|Imperative Programming]] while making use of OO and functional programming

- Uses [[Suppliers and Consumers\|Suppliers and Consumers]]

```java
<R> Stream<R> mapMulti(BiConsumer<T, Consumer<R>> mapper)
```

FlatMap: function from element to stream of new elements

mapMulti: biConsumer of element and consumer of the new elements

# Example Compared to flatMap

```java
List<String> nameSurnames(List<Person> ps){
	ps.stream()
		.flatMap(p->Stream.of(p.name(),p.surname()))
		.toLIst();
}


```

```java
// Returns list of all kittens
return cs.stream()
	.<Cat>mapMulti( (cat,c) -> cat.kittens().forEach(c))
	.toList();
```

## All Expression Are Equivalent in place of above

```
ki-> c.accept(ki)
c::accept
c
```