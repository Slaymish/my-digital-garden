---
{"dg-publish":true,"permalink":"/cybr-assignment-2/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

Using AWS Instance - Same as [[NWEN243 Project 1\|NWEN243 Project 1]]

# [[Buffer Overflow Attack\|Buffer Overflow Attack]]

## Creating a Malicious Input

1. Calculate the offset needed

Distance between the *base of the buffer* and the *return address*
This will be the size of the buffer + 4 (4 being the size of the previous frame pointer)

> [!Frame Pointer size]
> For 64bit OS's, the framepointer is 8bits instead of 4

- Use [[Debugging with GDB\|GDB]]
	- use `-g`
	- b foo
	- run
- Place a breakpoint at the foo fn

> [!Important]
With Ubuntu 20.04, you must use
"next" after "run"; otherwise,
the values will not be correct.

2. Find the address to place the shellcode

To increase the chances of jumpignt to the correct address, we fill the `badfile` with `NOP` (`0x90`), and place the malicious code at the *end* of the buffer

NOP: No operation command. Just goes to next instruction


Make the address offset + x. X being a large number (around 100-120)

- add 1-2 bytes if you keep getting segmentation fault

> [!Title]
> Can't have a 0 in return address in payload.
> Because it would terminate the buffer from getting copied
> (End of string terminator)