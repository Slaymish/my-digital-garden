---
{"dg-publish":true,"permalink":"/nwen-2021-final-test/"}
---

Related: #programming #practise 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Section A

1. -

```
a) #define SPEED 3.25e-26f OK
b) long XX double
c) 3 * 5 = 15 XX 5 30
d) #define FUNC(A,B) ((a) * ((b)-1))
e) 1 2 4 5 7 8 
```

2. -

```
a) int iarray[100] = {1,2,3,4};
b) #define STRING "Hello, world"
c) No because you the pointer is not able to point to two different memory addresses
d) 
	i) 10
	ii) 4
e) 
	i) numeric value of the expr sarray = 100
	ii) 102
	iii) 2
	iv) 3
	v) 203
```

3. -

```
a) 
	i) 1
	ii) struct car c1 = {maker:maker.audi, model:"a4"};
	iii) c1.info.age would be zero as the size of the union is only the size of the largest object
	iv) 32 + 2  = 34?
```

```C
//b)
struct node currentNode = head;
while(currentNode != NULL){
	printf("%d\n",currentNode->data);
	currentNode = currentNode->next;
}
```

4. -

```
a)
A memory leak occurs when you lose a pointer thats pointing to allocated memory. As theres no pointer pointing to it, it can remain unfreed and evetually build up and result in undefined program behaviour.

b)

```
