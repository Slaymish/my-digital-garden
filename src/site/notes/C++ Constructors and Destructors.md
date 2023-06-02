---
{"dg-publish":true,"permalink":"/c-constructors-and-destructors/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-05-2023
***

# Constructors

Info on constructors in C++ [[C++ Classes#Constructors\|here]]

- if no user declared constructors, compiler will add a **default constructor** and a [[Copy Constructor\|Copy Constructor]]

# Deconstructors

- As soon as created object gets out of scope, destructor will be called
- Eg at end of method its declared in

```C++
class A{
	~A(); // destructor
}
```

