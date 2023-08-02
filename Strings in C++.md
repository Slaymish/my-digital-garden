---
dg-home: false
dg-publish: true
---
Related: #programming 
Contents: [[NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 21-05-2023
***

# String in C++

- Similar to java string
- Except java strings are mutable
- Can do everything you can do with [[NWEN Strings\|C Strings]]
- [[C++ Standard Library]] String class - `std::string`
	- A container for handling char arrays

- Include `<string>` header file

```C++
#include <string>

int main()
{
	string s1, s2;
	s1 = "hello";
	s2 = "world!";
}
```