---
{"dg-publish":true,"permalink":"/c-standard-library/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Standard Library

## I/O In C++

- Based on streams


***

## Standard Output

```C++
#include <iostream>
int amin()
{
	std::cout<<"Hello World"; // Will print hello world
}
```

==std== = namespace where cout is defined
==cou==t = Object used to display output
==<<== = Insertion operator

## Standard Input

```C++
#include <iostream>
int main()
{
	int i;
	std::cin>>i;
	
	std::cout<<"You entered"<<i;
}
```

cin = Object used to read input



[[Strings in C++\|Strings in C++]]