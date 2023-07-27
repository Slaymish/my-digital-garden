---
{"dg-publish":true,"permalink":"/find-what-system-calls-are-invoked-in-a-c-program/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Find System Calls used by program

## Two commands
1. `ltrace` - traces call to library functions
2. `strace` - traces system calls

> [!INFO]
> Use `man <command-name>` to find info about a command
> Example: `man ltrace`


# ltrace usage

```shell
ltrace ./<program executable file>

ltrace -S ./<program executable file> (also displays Kernel system calls)
```

