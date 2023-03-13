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

### Examples
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

