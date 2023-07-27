---
{"dg-publish":true,"permalink":"/fork/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

- Used for challenge in assignment 3

# fork()

In linux, **all** processes are created with the system call fork()

```C
#include <sys/types.h>
#include <unistd.h>

pid_t fork(void); // return PID
```

- A process calling fork() spawn a new process (child), which is a **copy** of the calling process

- After the fork() call, two copies of the original code will be running

- Child is given a [[process ID\|PID]] of 0

# Using Fork

```C
void main(void)
{
	printf("Before fork\n");
	pid_t p = fork();
	printf("p = %d\n", p); // p = 13434
}
```

## Output (if Fork is successful)

```shell
Before fork
p = 13434 // from parent
p = 0 // From new child
```

- Order is not predictable

## Using the return Value

```C
void main(void)
{
	printf("Before fork\n");
	pid_t p = fork();
	if(p < 0) { /* Failed to fork */ }
	else if(p == 0 ){
		/* child process will execute this part */
	}
	else if(p > 0){
		/* parent process will execute this part */
	}
}
```

# Variables

- Variables that change in one process, don't effect the other process

```C
void main(void)
{
	int a = 10, b = 20;
	printf("Before fork\n");
	pid_t p = fork();
	if(p < 0) { /* Failed to fork */ }
	else if(p == 0 ){
		/* child process will execute this part */
		a++;
	}
	else if(p > 0){
		/* parent process will execute this part */
		b++;
	}

	printf("%d %d\n", a, b);
}
```

## When P = 13434 (parent process)

```
a = 10
b = 21
```

## When P = 0 (child process)

```
a = 11
b = 20
```

***

# Fork Bomb

```C
void main(void)
{
	while(1)
		fork();
}
```

- Continually create processes
- Use up all of machines resources
- Could cause machine to hang