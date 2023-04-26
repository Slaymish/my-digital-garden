---
{"dg-publish":true,"permalink":"/nwen-system-calls/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

| Lvls    |              |
| ------- | ------------ |
| Highest | Users        |
|         | Applications |
|         | OS           |
| Lowest  | Hardware     |


## System resources
- Physical
	- Eg input devices, screen displays etc
- Virtual
	- Eg Files, network connections, threads etc


- OS does **not** allow applications to access system resources directly

***

# System Call invocations

### System Call invocation example

```C
#include <stdio.h>

void main(void)
{
	printf("Helhgeivhsn");
	exit(0);
}
```

## printf()
- Standard C library makes system call invocation
	- write()
	- in user mode
- System call interface receives request
	- sys_write()
	- in kernel mode



# System call interface
- App devs do not have direct access to system calls
- Can access through system call api
