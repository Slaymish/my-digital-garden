---
{"dg-home":false,"dg-publish":true,"permalink":"/debugging-with-gdb/","dgPassFrontmatter":true}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***
```C
void swap(int a, int b)
{
	int temp = a;
	a = b;
	b = temp
}

void main()
{
	int i = 2;
	int j = 5;
	swap(i,j); // Swap doesn't work without pointers
}
```

```shell
gcc swap.c -g -o swap // '-g' compiles with debugging
gdb ./swap
run
```

*add '-pg' to compiler to look at time profile*
	use `grpof` to run output

**GDB  debug commands:**
- `l` prints code
- `break <linenum>` adds a breakpoint at linenum
	- or `br <linenum>`
- `print <var>` Print var value
- `print &<var>` print memory address of var
- `print *<pointer>` Dereferencing a pointer
- At breakpoints
	- `next` = Steps into functions
	- `step` = Goes over functions




