---
{"dg-publish":true,"permalink":"/swen-making-abstractions/"}
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