---
{"dg-home":false,"dg-publish":true,"permalink":"/nwen-241/nwen-structures/","dgPassFrontmatter":true}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

- A *struct* is a derived data type composed of members that are each basic or derived data type
- A single *struct* would store the data for one object

### Syntax to declare a structure:
```C
struct structure_tag {
	type1 member1;
	type2 member2;
	...
} variable_list;
```

- structure_tag = name of the structure
- structure_tag and variable_list are optional
- If structure_tag is not specified, variable_list should be
 
### Structure members can be:
- Basic data types
- Derived and user-defined types
- Pointers to basic, derived and user-defined data types

***


# Examples
```C
struct student_info { // Named struct
	char name [20];
	int student_id;
	int age;
}; // does not reserve any space
```

```C
struct student_info { // Named struct
	char name [20];
	int student_id;
	int age;
} s, t; // reserves space for s and t
```
- Variables of type struct student_info


#### Declaring a variable struct current_student
```C
struct student_info current_student;
```

#### Declaring an array of structs
```C
struct student_info nwen241class[250];
```
- Reserves space for 250 element array of records (structs)

***

# Creating New User Defined Types

- can define a struct as a new data type
- Instead of having to write struct student_info everytime
```C
typedef struct {
	char name [20];
	int student_id;
	int age;
} StudentInfo // alias
```

- Now can use that alias to assign var to the struct
```C
StudentInfo current_student;
```

### Initializing Structs
- At declaration
```C
typedef struct {
...
} StudentInfo

StudentInfo current_student = {"John Doe", 12345678, 18};
StudentInfo another_student = {"John Doe", 12345678}; 

// Designated Initialization
StudentInfo s1 = { .age = 18, .name = "John Doe"};
// or
StudentInfo s2 = { age: 18, name: "John Doe"};
```
- Remaining fields get set to 0

***

# Accessing/Manipulating structs
- Can reference a component of a struct with the *direct component selction operator*, which is a period
```C
strcpy(student1.name, "John Smith");
student1.age = 18;
printf("%s is in age %d\n", student1.name, student1.age)
```

- Can copy an entire struct
```C
student1 = student2;
```

***

# Passing structs to Functions

```C
typedef struct {
	char name[20];
	double diameter;
	int moons;
	double orbit_time, rotation_time;
	
} planet_t;
```

- When a struct var is passed as an input argument, all component values are **copied** into the local structure variable




