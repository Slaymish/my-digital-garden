---
{"dg-publish":true,"permalink":"/buffer-overflow-attack/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Buffer Overflow

## History

- A programming **bug** allows a buffer to extend beyond its defined length
- First documentation of attack was in 1972

## Memory Layout

[[Memory\|Memory]]

- Ram is primary storage, but can't interact directly with it
- OS provides you with a [[Virtual Address\|Virtual Address]] 
	- That gets translated to a [[Physical Address\|Physical Address]]
	- Donesn't use physical address for safety, plus it allows processes to only use what they need

![Pasted image 20230905180520.png](/img/user/Pasted%20image%2020230905180520.png)

Each [[NWEN Processes\|Processes]] virtual addresses aren't connected. IE They both have the same [[Virtual Address\|Virtual Address]], but it points to different [[Physical Address\|Physical Address]]

## Program Memory Stack

[[NWEN241/NWEN241 MOC\|NWEN241 MOC]]

- ==Global variables== stored in **Data segment**
- ==Uninitialised static variables== stored in **BSS**
- ==Dynamic memory== allocated to **heap**
- ==Local variables== stored in **Stack**

```C
int x = 100; // stored in Data segment
int main()
{
	int a = 2; // Stored in stack
	float b = 1.5;

	static y; // BSS

	// Stoed in heap
	int *ptr = (int *)malloc(2*sizeof(int));

	ptr[1] = 5; // stored on heap
	ptr[2] = 6;

	free(ptr); // free memory from heap

	return 1;
}
```

## Stack Frame

- When you invoke main, the system will create a **stack frame** for it
- When a method inside main is called, get another stack frame
	- `ebp` gets moved to that frame, though original position is stored
	- So can go back when done in that method
	- Stored in  [[Stacks and Interrupts#The System Stack\|The System Stack]], address stored in the `return` line

```C
void func(int a, int b)
{
	int x,y;

	x = a+b;
	y = a-b;

	return 0;
}
```

### Frame Pointer

- Lets programs view/manipulate memory, relative to this
	- (instead of uses the global address)
- Aka Base pointer or `ebp`

Add to it to go **up** the stack frame
Subtract form it to go down

![Pasted image 20230905182140.png](/img/user/Pasted%20image%2020230905182140.png)

### Copy Data to Buffer

```C
char src[40] = "Hello!!";
char dest[40];

strcpy(dest,src);
```

- strcpy stops at `\0`
- Compiler automatically injects `\0` at the end of each string

## Buffer Overflow Example

```C
void foo(char *str)
{
	char buffer[12];
	strcpy(buffer,str);
}

int main()
{
	char *str = "This is a masssiveee strihgn";
	foo(str);
		
	return 1;
}
```

- It won't stop writing to buffer
- Grows from the bottom of stack frame up
- After a certain point, it will **overwrite** the Frame pointer, and return address

![Pasted image 20230905183725.png](/img/user/Pasted%20image%2020230905183725.png)

### Possible Consequences

Overwriting ==return address== with some random address can cause:

1. Invalid/non-existing address
2. Invalid instruction
3. Access violation (valid instruction, but kernel)
4. ==Attackers code== -----> Malicious code to gain access

