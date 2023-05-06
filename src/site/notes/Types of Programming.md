---
{"dg-publish":true,"permalink":"/types-of-programming/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 05-05-2023
***

# Abstractions

## Imperative Programming

*Relying on nulls + ifs*

```java
class Stack { // could use records here
	int top;
	Stack tail;
	Stack(int top, Stack tail){this.top=top; this.tail = tail; }

	Stack push(int i) {return new Stack(i, this); }

	static Stack push(Stack ss, int i){
		if(ss != null) { return ss.push(i); }
		return new Stack(i,null);
	}
	// and equals, hashCode, toSring
}

Stack s0 = null; 
Stack s1 = new Stack(1, null); // [1]
Stack s2 = new Stack(1, new Stack(2,null)); // [1,2]
Stack s3 = Stack.push(s1, 5); // [5,1]
Stack s4 = s1.push(5); // [5,1], but with risk; what if s1 is empty?


if(s0 == null){System.out.println()"<Empty>");}
else { System.out.println(s0.top()); }
```

## Functional Programming

```java
record Stack(int top, Optional<Stack> tail) {
	Stack push(int i) {return new Stack(i, Optional.of(this)); }

	static <T> Optional<Stack> empty() { return Optional.empty(); }
	static <T> Option<Stack> of(int i) { return Optional.of(new Stack(i,empty()));}
	static Optional<Stack> oPush(Optional<Stack> os, int i){
		return Optional.of(new Stack(i,os));
	}

}

Optional<Stack> s0 = Optional.empty();
Optional<Stack> s0 = Stack.empty(); 

Optional<Stack> s1 = s0
	.map(s -> s.push(1)).or(()-> Stack.of(1)); // [1]

Optional<Stack> s1 = Stack.oPush(s0,1); // [1]

Stack sure_s1 = new Stack(1,s0); // [1]
Stack many = sure_s1.push(2).push(3); // [3,2,1]

s0.ifPresentOrElse( // no more if
	s->{ System.out.println(s.top());},
	()->{ System.out.println("<Empty>"); }
);

// we compose two lambdas together instead
```

## OO Programming

*What we're learning in this subject*

```java
interface Stack {
	static Stack empty(){ return new Stack(){}; }
	default int top(){ throw new Error("..."); }
	default boolean isEmpty(){ return true; }

	default Stack push(int top) {
		Stack self = this;
		return new Stack(){
			public int top(){ return top; }
			public Stack tail(){ return self; }
			public boolean isEmpty(){ return false; }
		};
	}
}

Stack s0 = Stack.empty();
Stack s1 = s0.push(1); // [1]
Stack many = Stack.empty().push(1).push(2).push(3); // [3,2,1]

if(s0.isEmpty()){ System.out.println("<Empty>");}
else{ System.out.println(s.top());}
// unsatisfactory, we still use an 'if' (imperative)
```

### Pure OO Programming

```java
interface Stack {
	static Stack empty(){ return new Stack(){}; }

	interface OnEmpty<R>{ R of(); }
	interface OnElem<R>{ R of(int elem, Stack tail);}

	default <R> R match(OnEmpty<R> a, OnElem<R> b){ return a.of(); }

	default Stack push(int top) {
		Stack self = this;
		return new Stack(){
			public <R> R match(OnEmpty<R> a, OnElem<R> b){ return b.of(top,self);}
		};
	}

	default int top(){ return match(
		()->{ throw new Error("...");},
		(top,tail)-> top
	);}

	default Stack tail(){ return match(
		()->{ throw new Error("...");},
		(top,tail)-> tail
	);}

	default boolean isEmpty(){ return match(
		()-> true,
		(top,tail)-> false
	);}

	default int size(){ return match(
		()-> 0, // base case
		(top,tail)-> 1 + tail.size() // inductive case
	);}

}

Stack s0 = Stack.empty();
Stack s1 = s0.push(1); // [1]
Stack many = Stack.empty().push(1).push(2).push(3); // [3,2,1]
System.out.println(many.size();)

System.out.println(s0.match(
	()->"<Empty>",
	(top,tail)->""+top
));
// no 'if' needed anymore!


// Contains 7 types
```

In imperative programming, unused method params are a bad idea
In OO they are a fundamental result of using dynamic dispatch to its full potential

## Difference between Functional and OO Programming

**Functional** is more about adding more visible types and reusing existing abstractions, like Optional so that you rarely write a new interface/implementations

**OO** is more about making your own interfaces/implementations, like how we wrote our own match implementation stead of relying on Optional for the support.
Inner auxiliary types like empty and non empty stack are often hidden


***

```java
// More stack operations

static List<Integer> toList(Stack s){
	return fillList(s, new ArrayList<Integer>());
}

static List<Integer< fillList(Stack s, ArrayList<Integer> l){ return s.match(
	()-> Collections.unmodifiableList(l),
	(top,tail)->{l.add(top); return fillList(tail,l); }
);}
```

- In good programming, its very common to have a facade public method calling a recursive private method doing most of the job