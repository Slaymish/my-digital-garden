---
dg-home: false
dg-publish: true
---
Related: #programming [[Process Initialisation on Linux]]
Contents: [[NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 27-02-2023
***

# wait() System Call

- Forces parent to suspend execution
	- Wait for child to terminate

```C
#include <unistd.h>
#include <sys/wait.h>

pid_t wait(int *status);
```

When child is terminated, it returns a **termination status**
If the status isn't NULL, the status gets returned to parent process

***

if &status is not NULL, wait() stores [[Status]] info in the int to which it points
