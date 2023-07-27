---
{"dg-publish":true,"permalink":"/equals-method/"}
---

Related: #
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 29-05-2023
***

# .equals

- In java, there's a **single** concept of equality
- Creates some difficult cases
	- Could accidentally call wrong one (when have [[SWEN221/Inheritance and Subtyping\|Inheritance and Subtyping]]\)

```java
boolean equals(Object other){ /* ...*/ }
```

- Even if in Student class, still use `Object` as param

## Best way to Implement

- Use [[SWEN221/SWEN_BasicJavaRecap#Records\|Records]] where possible
	- They implement equals and hashCode automatically
- Or can implement manually

### Manual Implementation

```java
class Person extends Object{
	String name;
	int age;

	Person(String name, int age){this.name =name; this.age=age;}

	public boolean equals(Object obj){
		if(this == obj){ return true; } // increases performance
		if(obj == null){ return false; } // this can't be null, as in method
		if(getClass() != obj.getClass()){ return false; }
		Person other = (Person) obj;
		return age == other.age && Objects.equals(name,other.name);

	}
}

class Student extends Person{
	List<Grade> gs;
	Student(String name, int age, List<Grade> gs){super(name,age); this.gs = gs;}

	public boolean equals(Object obj){
		if(this == obj){ return true;} // again, just performance
		this (!super.equals(obj)){ return false; } // checks above method
		if(getClass() != obj.getClass()){ return false; } // checks its a student
		Student other = (Student) obj;
		return Objects.equals(gs,other.gs); // check the new field
	}

}
```

- `==` only checks the object reference
- Only use `name.equals(name)` if fields cannot be meaningfully null
- Or use `Objects.equals(a,b)` 
	- Removes if null check need


<p align="center">
Enums can be compared with just ==
</p>

## Floats and Doubles

```java
/* Floats */

// Best way to check 
Float.floatToRawIntBits(weight) == Float.floatToRawIntBits(other.wieght)

// If you don't care about NaN
Float.floatToIntBits(weight) == Float.floatToIntBits(weights)


/* Doubles */

// Same methods
Double.doubleToRawLongBits(num)
Double.doubleToLongBits(num)
```

<h2 align="center">

Issues with uses instanceof

</h2>

- Consider **all** cases

```java
new Student("Bob", 21, List.of())
	.equals(new Person("Bob",21));
	
new Person("Bob", 21)
	.equals(new Student("Bob",21,List.of())); // this test fails


Student.equals(Object obj){
	if(!super.equals(obj)){ return false; }
	if(!(obj instanceof Student s)){ return false; }
}
```

# .equal Formal Properties

- It is **reflexive**
	- For any non-null ref value x, x.equals(x) should return true
- It is **Symmetric**
	- For any non-null ref value x and y, if x.equals(y) then y.equals(x)
- it is **transitive**
	- For any non null ref values x,y,z,
	- If x.equals(y) and y.equals(z) then x.equals(z)
- It is **consistent**
	- For any non-null ref value x and y
	- Multiple invocation of x.equals(y) consistently returns the same
	- Provided no information used in equals on objects is modified
- For any non-null ref value x, x.equals(null) should return false

# .hashCode Formal Properties

- Must consistently return the same **integer**, provided nothing used in equals comparisons on the objects is altered
- If two object are .equals(), then hashCode on those two objects must return the same integer result