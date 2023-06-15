---
{"dg-publish":true,"permalink":"/swen-221/swen-basic-java-recap/"}
---


# SWEN_BasicJavaRecap

Related: #java 
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
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
- All fields are private and [[SWEN221/Post-it Model#^c37b3f\|Post-it Model#^c37b3f]]
- [[Shallow Immuteable\|Shallow Immuteable]]

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
![SCR-20230301-kge.png](/img/user/SCR-20230301-kge.png)


<p align="center">
Fields are updated
</p>
<p align="center">
Objects are mutated
</p>


- Related to [[SWEN221/Post-it Model\|Post-it Model]]


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
- use [[SWEN221/Super constructors\|Super constructors]] instead

***

# Use [[StringBuilder\|StringBuilder]] instead of String

- When doing a lot of appends

