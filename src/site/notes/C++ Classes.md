---
{"dg-publish":true,"permalink":"/c-classes/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 12-05-2023
***

# Classes

## Defining a Class

```C++
class class_identifier {
	class_member_list
};
```

## Member Access Specifiers

If unspecified, default is **private**

- Public
	- Can use insides anywhere
	- [[C++ Inheritance\|Inherited]] by descendant classes
- Private
	- Can only use inside class
	- Not accessible by descendant classes
- Protected
	- Used in class inheritance

### Example

- const at end of function specifies it can not 

```C++
class Time {
public:
	void set(int,int,int);
	void print() const; 
	// const mean fn can't alter var in class
	Time(); //constructors
	Time(int,int,int); //constructors with args

	// these are all prototypes, 
	// don't have to define them here


private:
	int hour;
	int minute;
	int second;
};
```

## Constructors

- Similar to java constructors
- When class performs [[C++ Dynamic Memory Allocation\|C++ Dynamic Memory Allocation]], [[C++ Constructors and Destructors#Deconstructors\|Deconstructors]] is also needed

- Default Constructor
	- Accepts no args
	- `class_name()`
- Parameterised constructor
	- Accepts args
	- `class_name(parameters)`
- Copy constructor
	- Copies another existing object
	- `class_name(const class_name &`
	- & = reference operator

### Example

```C++
class student_info {
		int student_id;
		string name;
	public:
		void printf();
	
		// default constructor
		student_info()
		{
			student_id = 0;
			name="Same";
		}
		student_info(int,string);
};


// parameterized constructor
student_info::student_info(int id,string s){
	student_id = id;
	name=s;
}
```

```C++
class myClass{
	int a;
	int b;
	public:
		myClass(){
			a = 0;
			b = 0;
		}
		// Parameterized constructor
		// Using initializer list
		myClass(int x, int y):a(x),b(y){}


		void setA(int x){
			this->a = x; // similar to 'this.a' in java
			// this pointer to refer to member of the obj
		}
}
```

***

