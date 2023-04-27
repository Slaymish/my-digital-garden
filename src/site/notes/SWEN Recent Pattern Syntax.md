---
{"dg-publish":true,"permalink":"/swen-recent-pattern-syntax/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-04-2023
***

# Pattern syntax
*need to turn previews on*
- Ways to declare local variable 'implicitly'

## Different ways to write
```java
if(obj instanceof Person(var n, Dog(var l)) && l.x() > 3d){
	System.out.println(l);
	// can use vars n and l in condition and body
}
```

```java
if(!(obj instanceof Point p)){
	throw new Error("Can't see 'p'");
}

System.out.println("Here p is: " + p);

// 'p' is now visible after the if
```

```java
var varName = obj instanceof Person(var n, Dog(var l))
				&& l.x() < 3d;

// 'l' and 'n' visible only in expression
```

# Switch patterns
- Switch is an *expression*
- All code after each -> must be returning the correct type

```java
String result = switch(obj){
	case null-> "ahfh";
	case Integer i-> "Integer: " + i;
	case Person(var n, Dog(var l) dog) when l.x()<3d ->
		"Sitting Dog: " + dog;
	case Person(var n, Dog(var l) dog) -> // can declare dog
		"Running Dog: " + dog;
	case Person(var n, Cat(var col)) -> // or not
		"Color: " + col;
	case Point(var x, var y) ->
		"Point.x: " + x;
	default -> // must always specify a default
		"Some other case";
};

System.out.println(result);
```

- 'when' 
	- allowing to add custom boolean checks to any 'case'
	- similar to && for switch patterns
