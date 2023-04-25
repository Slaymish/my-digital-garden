---
{"dg-publish":true,"permalink":"/nwen-interprocess-communication/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***


# Whats a process?

| Program                                            | Process                                        |
| -------------------------------------------------- | ---------------------------------------------- |
| A set of instructions to do a task                 | A program in execution                         |
| Passive entity                                     | Active entity                                  |
| Stored in disk; doesn't require any other entities | Requires system resources (eg cpu, memory etc) |
| Life span - longer                                 | Life span - limited                            |

*Each time a program is run a new process is created*


## Process lifecycle
- new
	- is being created
- ready
	- waiting to be assigned to a processor
- running
	- instructions are being executed
- waiting
	- waiting for some event to occur
- terminated
	- finished execution


### System process commands



## Interprocess communication
