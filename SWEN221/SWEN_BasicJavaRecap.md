---
dg-home: false
dg-publish: true
---

# SWEN_BasicJavaRecap

Related: #java 
Contents: [[SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 02-03-2023
***

## Structure

- packages
	- classes, enums, interfaces, annotations, records
		- methods, fields, constructors etc
			- method local inner classes
			- statements
				- expressions
				- anonoymous inner statements



**Method Call expression**
- Receiver: System.out
	- Name before dot
- Method name
- actual arguments

**assert keyword:**
- Checks if statement is true
- If false, will throw exception
- Formatted similar to tenery boolean

```java
//eg
assert List.of(new Person("Bob",27)).contains(bob):"OK NOW!";
```

# Records

- Does a lot of boilerplate code for you
	- Changes .toString()
	- Removes need for constructors
- All fields are private and [[Post-it Model#^c37b3f]]
- [[Shallow Immuteable]]

```java
public record Person(String name, int age) 
{
	public String greet(String other){
		return "Hi " +other+ " I'm " + this.name;
	}
}

System.out.println(bob); // Prints Person[name=bob, age=27]
```

- Can add diff constructors

```java
record Person(String name, String surname, int age, List<Person> friends)
{
	Person(String name, String surname, int age)
	{
		this(name,surname,age,new ArrayList<>());	
	}
}
```

- Can override methods in records

```java
// Eg .toString()
String toString(){
	return this.first + " " + this.last;
}
```

***

# Aliasing

- When two local variables or fields reference the same object
- Aliasing on immutable data is harmless.
![[SCR-20230301-kge.png]]


<p align="center">
Fields are updated
</p>
<p align="center">
Objects are mutated
</p>


- Related to [[Post-it Model]]


***

# Sub-classes

```java
class Point{
	int x,y;
	...
}

class Point3D extends Point{
	int z;
	
}

```

- Dont repeat fields in sub-classes
- use [[Super constructors]] instead

***

# Use [[StringBuilder]] instead of String

- When doing a lot of appends

