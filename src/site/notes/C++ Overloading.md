---
{"dg-publish":true,"permalink":"/c-overloading/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

- Create two or more member having the same name declared in the same scope

# Function (method) Overloading

- Two or more functions with same name, but diff params

```C++
class Cal{
	public:
		int add(int a, int b);
		int add(int a, int b, int c);
}
```

# Operator Overloading

- `endl == '\n'`

Overloading the `<<` (extraction) operator

```C++
int b = 5;
cout<<"a== "<<endl<<b; 
```

- Can take multiple datatypes


