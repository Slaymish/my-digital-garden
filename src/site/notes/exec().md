---
{"dg-publish":true,"permalink":"/exec/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# exec() System Call

Replaces a current proccess' image with a new one
(load a new program within current process)

Upon achieving success, the exec() function does not return to the calling program. If it does return, it is an indication that the call has failed due to reasons such as non-existent file or bad permissions, among others.

There **no** system call by the name exec(), its a family of calls:
- `int execl(char *path, char *arg, ...);` // list
- `int execv(char *path, char *argv[]);` // array
- `int execle(char *path, char *arg, ..., char *envp[]);` // list + env var
- `int execve(char *path, char *argv[], char *envp[]);`
- `int execlp(char *file, char *arg, ...);`
- `int execvp(char *file, char *argv[]);`

All of these calls allow a process to replace itself with a new process by loading a new program into memory and starting its execution. 

```C
int execl(char *path, char *arg, ...)

// path = path of executable binary
// arg = list of one or more pointers of argument list to the program to be executed, end with NULL pointer
```

```C
void main(void) // typically exam question
{
	printf("Before exec\n");
	int r = execl("/bin/ls","ls",NULL); // lists all files in folder
	//printf("r = %d\n", r); this wouldn't get run, as instruction are replaced
}
```