---
{"dg-publish":true,"permalink":"/virtualisation/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 07-09-2023
***

# Virtualisation

- Fondation of [[Cloud Computing\|Cloud Computing]]
- Deteches the OS from the hardware


- [[Virtual Machines\|Virtual Machines]] first used in IBM mainframes in *1972*
- Allowed multiple users to share a [[batch-oriented system\|batch-oriented system]]

Is **not** [[emulation\|emulation]]. The Apps/Processes are still running on original hardware, just in a container. Emulation recreates the system calls and processor architecture.

## Definition

- VM provides env for programs that's identical to the original machine
- Program show only minor performance decreases (if any)
- Uses a [[VMM\|VMM]]  to manage system resources

### Make up of a VM

1. Configuration file
	1. How many virtual processor
	2. Ram?
	3. What I/O devices it has access to
	4. Storage

