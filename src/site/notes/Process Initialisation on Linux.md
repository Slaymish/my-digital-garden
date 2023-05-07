---
{"dg-publish":true,"permalink":"/process-initialisation-on-linux/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Process Initialisation

- The init process is the parents of **All processes**, executed by the kernel during boot

- A process is created by another process, which create more processes

- Every process (except init) has a parent

- Every process has a [[process ID\|process ID]] (pid)


Creates a Process [[Year 1/COMP103/Trees\|tree]]

# Linux Ps Command

```shell
ps
```

- Shows what processes are running on your machine


***

# Process Management system calls

- All processes are created with the system call [[fork()\|fork()]]

- [[exec()\|exec()]]

- wait()

- exit()
