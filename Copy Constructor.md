---
dg-home: false
dg-publish: true
---
Related: #
[[UNI MOC]]
Hamish Burke || 24-05-2023
***

- Creates a new object from the same classes existing object

# Java

```java
class Person{
	public Person(Person other){
		this.name = other.name();
		this.age = other.age();
	}
}
```

# C++

## When Used

- When defining an object
- When an object is passed a value by a function

```C++
class StudentInfo{
	int student_id;
	string name;

public:
	

}

StudentInfo s1;
StudentInfo s2;
```