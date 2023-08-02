---
dg-home: false
dg-publish: true
---
Related: #programming 
Contents: [[NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 24-05-2023
***

# Dynamic Memory Allocation

- Similar to [[NWEN Dynamic Memory Management]]

## Using malloc() in C++

- C allows pointers to be implicitly converted to any other pointer type

```C++
// Valid in C NOT C++
// C allows pointers to be implicity converted to any other pointer type
int main(){
	int *p;
	p = malloc(sizeof(int));
	*p = 5;
	printf("%d",*p)
}

// Valid in BOTH
int main(){
	int *p;
	p = (int*)malloc(sizeof(int));
	*p = 5;
	printf("%d",*p)
}
```

***

- C++ uses **new** and **delete** operators to create/destroy dynamic variables
- They call the[[C++ Constructors and Destructors]] of objects respectively
- On failure, new throws bad_alloc exception

## New Operator

- Allocates memory for the variables and returns a pointer to it

```C++
new datatype;
```

## Delete Operator

- Free memory that was allocated using *new*

```C++
delete ptr;

delete [] ptr; // Deallocates memory block pointed to by prt(array)
```


