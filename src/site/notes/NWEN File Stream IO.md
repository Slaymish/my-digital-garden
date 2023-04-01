---
{"dg-publish":true,"permalink":"/nwen-file-stream-io/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

I/O = The process of copying data between main memory and external devices


## In C
- Each file is a sequential stream of bytes
- C imposes no structure on a file


# Accessing Files
- Must open first
	- Establishes a communication channel

## Communication channel
*Can be a file stream or a file descriptor*

- C provides functions for accessing files:
|                    | File Descriptor                                             | File Stream                                                    |
| ------------------ | ----------------------------------------------------------- | -------------------------------------------------------------- |
| Content access     | Primitive access: contents can be access as blocks of bytes | Rich access: contents can be formatted using format specifiers |
| Control operations | Allows setting of control params                            | Does not allow                                                 |
| Special I/O modes  | Allows special access modes such as non-blocking            | Does not allow                                                 |
| Buffering          | None                                                        | Supports 3 modes of buffering                                  |


- For special files (eg I/O devices and sockets)
	- [[File descriptor\|File descriptor]] is the recommended approch

- For regular files (files on disk)
	- [[File stream\|File stream]] recommended


