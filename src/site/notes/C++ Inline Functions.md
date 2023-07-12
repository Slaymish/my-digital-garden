---
{"dg-publish":true,"permalink":"/c-inline-functions/"}
---


Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 12-05-2023
***

# C++ Inline Functions

Including the implementation of a function within the [[C++ Classes\|class]] definition is an implicit **request** to make a function *inline*

## When a Function is Inline

- The compiler does not make a function call
- The code of the function is used in place of the function call
- Compiled code might be larger, but will execute faster

### To Explicitly Request

- Add inline keyword before return type in function declaration and definition

```C++
class Time {
	public:
		inline void print() const;
		void set(int h, int m, int s){
			hour = h;
			minute = m;
			second = s;
		}
}

inline void Time::print(){
	printf("%d:%d:%d\n",hour,minute,second);
}
```



