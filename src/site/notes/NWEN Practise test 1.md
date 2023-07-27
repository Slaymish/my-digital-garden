---
{"dg-publish":true,"permalink":"/nwen-practise-test-1/"}
---


# NWEN Practise Test 1

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

- 1-

```
a)
enum {low,medium,high}; OK

b)
enum difficulty {low, medium, high}; OK

c)
enum fruit {apple, banana = 4, orange}; OK


d)
enum fruit myfruit; OK
myfruit = apple;

e)




```

```C
FILE *fp = fopen("input.txt","r");

```

- create pointer fp, use fopen(data,mode);
- if (fp == NUL){print failed; return 0;}
- while(c=fgetc(fp) != EOF) 

```C
int c = 100;

FILE *out = fopen("helh.txt","w");
if(out == NULL){
	printf("Faiuled to create file");
	return 0;
}
fputc(c,out);

fclose(out);
return 0;
```