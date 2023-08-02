---
dg-home: false
dg-publish: true
---
Related: #programming 
Contents: [[NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 27-02-2023
***

| Lvls    |              |
| ------- | ------------ |
| Highest | Users        |
|         | Applications |
|         | OS           |
| Lowest  | Hardware     |

# System Resources

- Physical
	- Eg input devices, screen displays etc
- Virtual
	- Eg Files, network connections, threads etc


- OS does **not** allow applications to access system resources directly

***

# System Call Invocations

## System Call Invocation Example

```C
#include <stdio.h>

void main(void)
{
	printf("Helhgeivhsn");
	exit(0);
}
```

# printf()

- Standard C library makes system call invocation
	- write()
	- in user mode
- System call interface receives request
	- sys_write()
	- in kernel mode

# System Call Interface

- App devs do not have direct access to system calls
- Can access through system call api

# System Calls

`#include <sys/type.h>`
`#include <sys/socket.h>`

- socket()
- bind()
- listen()
- accept()
- connect()
- sent()/recv()
- close()

Used to make a [[NWEN Sockets#^02aff4\|TCP server]]

