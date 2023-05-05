---
{"dg-publish":true,"permalink":"/nwen-241/nwen-pointers/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Word-addressable Architecture:

- Every memory location corresponds to one word
- Used in the past

# Byte-addressable Architecture:

- Every memory location corresponds to one byte
- Size of address depends on num of bits used by CPU for addressing
	- Eg a CPU that uses 32 bits for addressing, an address has 32 bits


***

# Memory Location and Variables

- A variable declaration allocates memory to store the value of the variable

```C
char c = 'A';
```

- Memory location 1001 contains value of variable c

> [! ]
> A variable **directly** reference a value

## Multi-byte Data

- A multi-byte var using the **starting address**
- same for [arrays](NWEN_Arrays)

***

# Declaring a Pointer

- Pointers are typed based on the type of entity they point to
- Address size is 4 bytes

```C
data_type *name;
```

## Examples

```C
int *p; // points to a int
float *q; // points to a flaot
char *r; // points to a char
int *s[5]; // s is an array of 5 int pointers
```

***

# Address Operator (&)

- Will return the memory location of the variable
- Variable can be any ordinary variable or even a pointer var

```C
int a, *x;
x = &a;
```

- assigns the address of a to x
	- ie x points to variable a

# Indirection Operator (\*)

- A pointer variable contains a memory address
- Refers to the contents of the variable that the pointer points to

```C
int a = 100, b, *x;
x = &a; // makes x point to a
b = *x; // sets b to 100
```

# Null Pointer

- can point a pointer to null so it isn't pointing to a random part of memory

```c
int a = 10, *x = null;
```

***

# Usage of Pointers

1. Accessing info stored in [[NWEN241/NWEN_Arrays\|arrays]]
2. Pass parameter to functions
3. Enable dynamic data structures

> [!Arrays and Pointers]
> Arrays are a [[NWEN241/NWEN_Arrays#^822933\|fixed pointer]]

# Ways to Access an Array

```C
int z[10], *ip;
ip = &z[0];
```

**The first elem of this arr can be accessed in all these ways**
- z[0]
- ip[0]
- \*z
- \*ip


***

# Pointer Arithmetic

- Addition and subtraction can be performed on pointers

```c
data_type *name;
name + k // evaled as name + k*sizeof(data_type)

name - k // evaled as name - sizeof(data_type)

// In general
int z[10];
z+i == &z[i]
```

***

# Traversing Arrays Using Pointers

**Usual Way**

```C
int a[] = { ... };
int len = sizeOf(a)/sizeof(int); // length of arr
for(int i = 0; i < len; i++){
	// do smth with a[i]
}
```

**With pointers**

```C
int a[] = { ... };
int len = sizeof(a)/sizeof(int);
for int *ip = a; ip < a + len; ip++){
	// do smth with *ip
}
```

# General (void) Pointers

- A void pointer is a pointer that can hold the address of any type of data.
- The void keyword is used to specify that a function returns nothing or that a pointer parameter points to a memory location of unspecified type.
- Void pointers are often used in generic programming, where the type of data being operated on may not be known in advance.
- A void pointer cannot be dereferenced directly; it must first be casted to a pointer of a specific data type before it can be used to access the data. 
- Void pointers are commonly used in memory allocation functions such as malloc(), calloc() and realloc().
- When a void pointer is casted to another pointer type, it is important to ensure that the types are compatible, otherwise undefined behaviour can occur.


***

# Pointer Types

- Pointer generally same size
- *Shouldn't* point a var of one type to a diff type
	- Only results in warning
- Can cast the pointer
	- Removes warning
	- Still shouldn't (unexpected outcomes)

## Accessing/Manipulating Struct Pointers

- Can reference a component of a struct with the **indirect component selection operator** (->)

```C
strcpy(sp->name, "John Smith");
sp->age = 18;
printf("%s is in age %d\n", sp->name, sp->age);
```

***

- When invoking a fn, the actual parameter (i,j) are copied to the formal params (a,b)
- Changing a/b doesn't change i/j

```C
void swap(int a, int b)
{
	int temp = a;
	a = b;
	b = temp;
}

int i = 5;
int j = 10;
swap(i,j);
printf("%d %d", i,j); // out= 5 10 (unchanged)

```

Solution:

# Call by Reference

- Pass a copy of the address to the function
- Both formal and actual parameters refer to the same address
- Done using pointers

```C
void swap(int *a, int *b)
{
	int temp = *a;
	*a = *b;
	*b = temp;
}
```

## Placing Restrictions

- Add const modifier to parameter

```C
void print_student(const StudentInfo *s)
{
	printf("Name %s\n", s->name);

	...


	s->age = 100; // compiler won't allow this
}
```