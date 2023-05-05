---
{"dg-publish":true,"permalink":"/nwen-241/nwen-process-layout/"}
---


# NWEN Process Layout

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

| Code Segment (Txt) |
| ------------------ |
| Data Segment       |
| Heap Segment       |
| free               |
| Stack Segment      |

## Code Segment:

- Contains programs machine code

## Data Spread Over:

- Data segment
	- Fixed space for global vars and constants
- Stack Segment
	- For temp data (eg local var in a fn)
	- Expands/shrinks
	- Origin of term (stack overflow)
- Heap Segment
{ #c40dd5}

	- For dynamically allocated memory
	- Expands/shrinks


