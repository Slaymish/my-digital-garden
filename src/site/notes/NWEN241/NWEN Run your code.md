---
{"dg-home":false,"dg-publish":true,"permalink":"/nwen-241/nwen-run-your-code/","dgPassFrontmatter":true}
---


Related: #programming #C 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
Hamish Burke || 27-02-2023
***

**To compile:**
```shell
gcc hello.c -o hello
```

- Creates a executable named 'hello'

**To run:**
```shell
./hello
```

- Can only run the compiled file
- './' means that the executable is at the current working directory

***
### Complilation Process:
1. Preprocessing Phase
2. Compilation Phase
3. Assembly Phase
4. Linking Phase


## cppcheck
- For C and C++ code that checks for coding errors, security vulnerabilities, and other issues that can lead to unexpected behavior or crashes.
- Can detect programming errors, including memory leaks, null pointer dereferences, uninitialized variables, and buffer overflows.

***

# GDB
*GNU Debugger*

- Can step through code

**Notes:**
- Developed by GNU Project
- Command-line interface
- Debugging tool for C, C++, Ada, and more
- Supports Linux, macOS, Windows (and other systems)
- Breakpoints and watchpoints
- Step-by-step execution
- Inspect variables and memory
- Evaluate expressions
- Call stack manipulation
- Extensible with Python and Guile
- Remote debugging support

- [[Debugging with GDB\|Debugging with GDB]]