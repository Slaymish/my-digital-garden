---
{"dg-publish":true,"permalink":"/nwen-closing-a-socket/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Closing a Socket

- Sockets must be closed after its use

```C
int shutdown(int sockfd, int how);

// How:
// can be SHUT_RD (further receptions disallowed), or
// SHUT_WR (further transmissions disallowed), or
// SHUT_RDWR (further receptions and transmissions disallowed)

// Shutdown blocks communication with destroying the socket

int close(int sockfd)

// Close blocks the communication and destroys the socket
```
