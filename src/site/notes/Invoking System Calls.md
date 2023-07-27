---
{"dg-publish":true,"permalink":"/invoking-system-calls/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Invoking System Calls

## Directly

- Making a call to a function built directly into the kernel

Need to know target architecture, written generally in assembly

## Indirectly

- Using a high-level application programming interface (API) that will invoke it
- Most common APIs:
	- Win32 API for Windows
	- POSIX API for POSIX-based systems (UNIX, Linux, Mac OSX)
	- Java API for the Java virtual machine (JVM)





