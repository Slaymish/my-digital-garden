---
{"dg-publish":true,"permalink":"/swen-term-test-4-prep/"}
---

Related: #
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 18-05-2023
***

# Term Test 4

<p align="center">
30th May, 5-7pm
</p>


- Will have 'negative questions'

- Clone api with reflection

## Notes

- Remember 'longest string' questions
- Look at Mock term test
- **Lab 8 questions**
- Remember [[Collection Operations\|Collection Operations]]!!!
	- They'll be on the test document
- can use `.new` as method (SpecialSyntax_Mini [hard])

## Reducing Stack Lab 8 Question

```java
interface Stack<E>{
	default E top() { throw new Error("Empty");}
	default Stack<E> pop(){throw new Error("Empty");}
	default ...
}

class Reduce{
	static <A,B> A of(A acc, BiFunction<A,B,A> f, Stack<B> bs){
		return bs.match(
			() -> acc, // on empty stack, return acc
			(e,t) -> of( // else we have an elem and tail
						f.apply(acc,e), // new acc = function result
						f, // same accumulator function
						t) // recursive call on tail
		);
	}
}
```

[[BiFunction\|BiFunction]]

## Bool Interface Question

- Declaring a static field and returning it

```java
interface Bool{
	Bool and(Bool other);
	Bool or(Bool other);
	Bool not();
	<R> R ifElse(Supplier<R> a, Supplier<R> b);
}

class True implements Bool {
	private True(){} // private constructor
	private static True instance = new True();
	public static True instance(){return instance;}
	public Bool or(Bool other){ return this; }
	public Bool not(){ return False.instance();}
	public <R> R ifElse(Supplier<R> a,Supplier<R> b){return a.get();}
}

class False implements Bool{
	private False(){} // private constructor
	private static False instance = new False();
	public static False instance(){ return instance; }
	public Bool or(Bool)
	
}
```

## Conceptual Steps

- Main problem division
	- Find max height
	- Select all towers with that height
- Refined problem division:
	- If possible find max height
		- if there is max select
		- ekse return empty list


***

```java

return ps.entrySet()
	.stream()
	.filter(x -> dangerLoc.contains(x))
	.flatMap(x -> x.getValue().stream())
	.toList();
	
return ps.entrySet()
		.stream()
		.filter(x -> dangerLoc.contains(x))
		.mapMulti(e,c) -> e.getValue().forEach(c::accept) // takes a consumer
		.toList();

```