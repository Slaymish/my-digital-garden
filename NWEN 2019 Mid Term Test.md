---
dg-home: false
dg-publish: true
---
Related: #programming #practise 
Contents: [[NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 27-02-2023
***

# Section A

1. ? 
2. ?
3. true X (false)
4. false OK
5. false X (true) // remaining elems are initiated to 0
6. true OK
7. false OK
8. false OK

# Section B

9. `char str[] = "Twelve";`
	- 7 OK
10. code won't compile X (3) // '0' acts as false
11. size of char X (sizeof(int)) // takes size of biggest type in union
12.  `2+9/3-2 = 2+3-2 = 5-2 = 3` OK
13. 0 OK
14. none of the above X (void) // generic pointers can be declared with void
15. a (i & iii) OK
16. c
17. c
18. c (address of operator) OK
19. d (0,0,0) OK
20. a

# Section C

21. - [[NWEN Run your code#^2995be]]

```
Linting
Compiling
Assembly
Running

XX

Pre-processing
Assembly
Compliation
Linking



```

22. -

```
?
```

23. -
a)

```
The difference is how you call them, as they are both pointers to the first value in the array. With str1, you'd called it with str[i], but with str2 its &str2[i]

XX

First is a string variable. Second points to a string literal
```

b)

```
printf("%s\n",str1[7]);

XX

printf("%c",str1[7]);
```

c)

```
print("%s\n",(&str2+(6*sizeof(char))));

XX

printf("%c",*(str2+7));
```

d)

```
#include <string.h> OK

for(int i=0;i<str1.length;i++){
	strcpy(str1[i],(str2+(i*sizeof(char)));
}

XX

strcpy(str1,str2);
```

24. -
a) 2305 OK
b) 2304 OK
c) 2305 XX 2304
d) 'g'
e) '#' XX 'g'



