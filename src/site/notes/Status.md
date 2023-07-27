---
{"dg-publish":true,"permalink":"/status/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Status C

Status integer can be inspected with **macros**:
- WIFEXITED(status)
- WEXITSTATUS(status)

***

```C
exit(es); // child returns its return status through exit

////

pid = wait(&es);
if(WIFEXITED(es)){ 
	// parents reads status sent by child through macros
	printf("Child exited, code: %d\n",WEXITSTATUS(es));
}

```

