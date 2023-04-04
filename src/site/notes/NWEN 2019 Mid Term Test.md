---
{"dg-publish":true,"permalink":"/nwen-2019-mid-term-test/"}
---

Related: #programming #practise 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Section A
1. ?
2. ?
3. true
4. false
5. false
6. true
7. false
8. false

# Section B
9. `char str[] = "Twelve";`
	- 7
10. code won't compile
11. size of char
12.  `2+9/3-2 = 2+3-2 = 5-2 = 3`
13. 0
14. none of the above
15. a (i & iii)
16. c
17. c
18. c (address of operator)
19. d (0,0,0)
20. a

# Section C
21. -
```
Linting
Compiling
Assembly
Running
```
22. -
```
?
```
23. -
a)
```
The difference is how you call them, as they are both pointers to the first value in the array. With str1, you'd called it with str[i], but with str2 its &str2[i]
```
b)
```
printf("%s\n",str1[7]);
```
c)
```
print("%s\n",(&str2+(6*sizeof(char))));
```
d)
```
#include <string.h>

for(int i=0;i<str1.length;i++){
	strcpy(str1[i],(str2+(i*sizeof(char)));
}
```
24. -
a) 2305
b) 2304
c) 2305
d) 'g'
e) '#'