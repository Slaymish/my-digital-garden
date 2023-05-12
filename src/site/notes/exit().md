---
{"dg-publish":true,"permalink":"/exit/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# exit() System Call

- Enables explicit call for normal termination
- It does cleanup and release of resources

```C
void exit(int status);
```

## [[Status\|Status]]

Integer between 0-255



