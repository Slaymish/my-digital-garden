---
{"dg-publish":true,"permalink":"/nwen-241/nwen-dynamic-memory-management/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

## Why?
- Don't know size of array ahead of time

***

# Dynamic Memory Allocation
- Allocated in the [[NWEN241/NWEN Process Layout#^c40dd5\|Heap Segment]]
- calloc()
	- Allocated array of memory
	- Return the address of the 1st byte 
		- Cast the returned address to the wanted type
	- Can return null if failed
	- Sets all values to 0
```C
void *calloc(size_t num, size_t esize)

// size_t = type used to indicate sizes, unsigned int
// num = number of elems to be allocated in the array
// esize = size (in bytes) of a single elem to be allocated
	// Use sizeof(<type>) to get the correct num

// Memory of size num*esize is allocated
```
In use:
```C
float *nums;
// set other vars ....
nums = (float *)calloc(a_size, sizeof(float));

if(num == NULL){
	/* exit etc */
}
```

- malloc()
	- allocate a single block of memory
	- NULL return if not enough memory available
	- **Doesn't** set all values to 0
Prototype:
```C
void *malloc(size_t esize);
```


- realloc()
	- Extend or reduce the amount of space allocated previously
	- ptr = pointer to memory previously dynamically allocated
	- esize = new size to allocate
	- NULL if reallocation fails
Prototype:
```C
void *realloc(void *ptr, size_t esize);
```
Example:
```C
...
nums = (float *)calloc(5,suzeof(float));
nums = (float *)realloc(nums, 10*sizeof(float));
// need to reassign nums to it

//increased size of memory to 10 (from 5)
```

- free()
	- free up a piece of memory thats no longer needed
	- If free memory allocated with calloc, entire array is released
	- Undefined behaviour if passed (could crash):
		- address of already freed memory
		- address of non dynamically allocated memory
Prototype:
```C
void free(void *ptr);
```
Example:
```C
float *nums;
...
num = (float *) calloc(a_size, sizeof(float));
...
free(nums); // num still pointing
```


> [!Memory Allocation]
> Dynamically allocated memory **doesn't** go away at end of fn's
> you MUST explicitly free it up


***

# Allocating Memory for 2d Arrays
- Allocate an array of pointers
- Make each pointer point to a 1D array
```C
float **A; // A = array (pointer) of float pointers
int X;

A = (float **) calloc(5,sizeof(float *)); // 1D array (size 5)

for (X=0;X<5;X++)
	A[X] = (float *) calloc(4, sizeof(float));

// A[X][Y] is the Yth entry in the arr that the Xth member of A points to
```

## Irregular-sized 2D array
- Benefit of using pointers
```C
float **A; // A = array (pointer) of float pointers
int X;

A = (float **) calloc(5,sizeof(float *)); // 1D array (size 5)

for (X=0;X<5;X++)
	A[X] = (float *) calloc(X+1, sizeof(float));
```


***

# Common issues
{ #53155f}


- Returning a pointer to an automatic variable
```C
int *foo(void)
{
	int x; // local var

	...

	return &x; // x doesn't exist outside of method

	// Pointing to invalid location
}
```

- Heap block overrun
	- Similar to an array going out of bounds
```C
void foo(void)
{
	int *x = (int *) malloc(10 * sizeof(int));

	x[10] = 10;
	/* only allocated up to x[9]*/

	free(x);
}
```

- [[Memory Leaks\|Memory Leak]]
	- Loss of pointer to allocated memory
```C
int *pi;

void foo(void)
{
	pi = (int*) malloc(8*sizeof(int));
	/* leaked the old memory pointing to pi*/

	free(pi);
}

int main(void)
{
	pi = (int*) malloc(4*sizeof(int)); // this will get lost
	foo();
}
```

- Potential memory leak
	- Loss of pointer to beginning of memory block
	- Can recover through pointer arithmetic
```C
int *ip = NULL;

void foo(void)
{
	ip = (int *) malloc(2*sizeof(int));
	...
	ip++;
	/* ip is not pointing to start of block anymore*/
}
```

- Free non-heap or unallocced memory
```C
void foo(void)
{
	int fnh = 0;
	free(&fnh); /* freeing stack memory */
}
```


# Valgrind
- Open source tool for detecting memory issues
