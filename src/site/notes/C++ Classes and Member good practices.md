---
{"dg-publish":true,"permalink":"/c-classes-and-member-good-practices/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

- Declare the class in a header file (.h)

```java
class Time {
	public:
		void set(int, int, int);
		void print() const;
		Time();
		Time(int,int,int);
	private:
		int hour;
		int minute;
		int second;
};
```

- Put the implementations of the member functions in the .cpp file