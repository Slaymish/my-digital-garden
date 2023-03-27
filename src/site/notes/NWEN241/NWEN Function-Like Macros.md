---
{"dg-publish":true,"permalink":"/nwen-241/nwen-function-like-macros/"}
---


Related: #programming #C 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***
Macro:
```C
#define SQ(x) x*x

int main(void)
{
	int sq = (int)SQ(5);

	return 0;
}
```

Issue:
```C
int main(void)
{
	int sq = (int)SQ(1+1);
}
```
- When above is pre-processed (-E with gcc)
```C
int main(void)
{
	int sq = (int)1+1*1+1;
}
```


Macro:
```C
#define SQ(x) x*x // 1
#define SQ(x) (x) * (x) // 2
#define SQ(x) ((x) * (x)) // 3
```

Example problematic usage:
```C
SQ(1+1) //1
(int)SQ(2.0) % 2 // 2
SQ(i++) //3
SQ(f()) //3

// No real way to fix num 3
```




