---
{"dg-home":false,"dg-publish":true,"permalink":"/nwen-241/nwen-pointers/","dgPassFrontmatter":true}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

## Word-addressable architecture:
- Every memory location corresponds to one word
- Used in the past

## Byte-addressable architecture:
- Every memory location corresponds to one byte
- Size of address depends on num of bits used by CPU for addressing
	- Eg a CPU that uses 32 bits for adressing, an address has 32 bits


***


# Memory Location and Variables
- A variable declaration allocates memory to store the value of the variable
```C
char c = 'A';
```
- Memory location 1001 contains value of variable c

> [! ]
> A variable **directly** reference a value

### Multi-byte data
- A multi-byte var using the **starting address**
- same for [arrays](NWEN_Arrays)

***

# Declaring a Pointer
- Pointers are typed based on the type of entity they point to
```C
data_type *name;
```

##### Examples
```C
int *p; // points to a int
float *q; // points to a flaot
char *r; // points to a char
int *s[5]; // s is an array of 5 int pointers
```

***

## Address Operator (&)
- Will return the memory location of the variable
- Variable can be any ordinary variable or even a pointer var

```C
int a, *x;
x = &a;
```
- assigns the address of a to x
	- ie x points to variable a

## Indirection Operator (\*)
- A pointer variable contains a memory address
- Refers to the contents of the variable that the pointer points to
```C
int a = 100, b, *x;
x = &a; // makes x point to a
b = *x; // sets b to 100
```
