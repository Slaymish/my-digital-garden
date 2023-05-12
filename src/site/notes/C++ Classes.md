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
- Private
	- Can only use inside class
- Protected
	- Used in class inheritance

### Example

- const at end of function specifies it can not 

```C++
class Time {
public:
	void set(int,int,int);
	void print() const; 
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
- When class performs [[NWEN241/NWEN Dynamic Memory Management\|dynamic memory allocation]], **destructor** is also needed

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
student_info:: student_info(int id,string s){
	student_id = id;
	name=s;
}
```

***

