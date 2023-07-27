---
{"dg-publish":true,"permalink":"/steam-map-multi/"}
---

Related: #
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

# Stream.mapMulti

## What is It?

- Takes a BiConsumer as an argument
- Inside the BiConsumer, you can invoke `Consumer::accept` as many times as you like

```java
List<Integer> integers = Arrays.asList(1, 2, 3, 4, 5);

```



***

- Allows use of [[Types of Programming#Imperative Programming\|Imperative Programming]] while making use of OO and functional programming

- Uses [[Suppliers and Consumers\|Suppliers and Consumers]]

```java
<R> Stream<R> mapMulti(BiConsumer<T, Consumer<R>> mapper)
```

FlatMap: function from element to stream of new elements

mapMulti: biConsumer of element and consumer of the new elements

## Example Compared to flatMap

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

***

## Using an Auxiliary Method

### With flatMap

```java
record Cat(List<Cat> kittens){}

Stream<Cat> allCatsAux(Stream<Cat> cs){
	return cs
		.flatMap(c -> Stream.concat(
			Stream.of(c),
			allCatsAux(c.kittens().stream())
		));
}

List<Cat> allCats(List<Cat> cs){ 
	return allCatsAux(cs.stream()).toList();
}
```

### With mapMulti

```java
record Cat(List<Cat> kittens){}

void allCatsAux(Cat cat, Consumer<Cat> c){
	c.accept(cat);
	for(Cat ki : cat.kittens()){
		allCatsAux(ki,c);
	}
}

List<Cat> allCats(List<Cat> cs){ 
	return cs.stream()
		.<Cat>mapMulti( (cat,c) -> allCatsAux(cat,c) )
		.toList();
}
```

# Other Uses

```java
// flatten optionals away
Stream<String> streamsOfOptionals( Stream<Optional<String>> oss) {
	return oss.mapMulti( Optional::ifPresent );
}
```

## Translating Nested-for Loops to mapMulti Streams

```java
// Translating nested for loop
List<Point< code(List<Point> ps) {
	List<Point> res = new Arraylist<>();
	for(Point pi: ps){
		if(pi.x < 0 || pi.y < 0){ continue; }
		for(Point pj : ps){
			if(pi == pj){ continue; }
			if(pj.x < 0 || pj.y < 0) { continue; }
			res.add(new Point(pi.x + pj.x, pi.y + pj.y))
		}
	}

	return Collections.unmodifiableList(res);
}
```

<p align="center">
Is the same as
</p>

```java
List<Point> code(List<Point> ps){
	return ps.stream()
		.filter(p-> p.x >= 0 && p.y >= 0)
		.<Point>mapMulti( (pi,res) ->{
			for(Point pj : ps) {
				if(pi==pj){continue;}
				if(pj.x < 0 || pj.y < 0){continue;}
				res.accept(new Point(pi.x + pj.y + pj.y))
			}
		})
		.toList();
}
```