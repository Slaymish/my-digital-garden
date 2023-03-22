---
{"dg-home":false,"dg-publish":true,"permalink":"/nwen-process-layout/","dgPassFrontmatter":true}
---

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


### Code segment:
- Contains programs machine code

### Data spread over:
- Data segment
	- Fixed space for global vars and constants
- Stack Segment
	- For temp data (eg local var in a fn)
	- Expands/shrinks
	- Origin of term (stack overflow)
- Heap Segment
	- For dynamically allocated memory
	- Expands/shrinks


