---
{"dg-publish":true,"permalink":"/nwen-host-and-network-byte-order/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

Some computers write data 'left-to-right' and other 'right-to-left'

a machine can read its own data just fine
- problems happen when one computer stores data and a different type tries to read it

# Little-endian

- Store the ==least== significant byte at the smallest memory address

# Big-endian

- stores the ==most== significant byte at the smallest memory address


***

C methods:

```C
uint32_t htonl(uint32_t hostlong);
uint16_t htons(uint16_t hostshort);
uint32_t ntohl(uint32_t netlong);
uint16_t ntohs(uint16_t nethshort);
```

***

# How to check endianness

- Use **lscpu** (linux)
- Write own C program

```C
#include <stdio.h>
void main(){
	int n = 1;
	// little endian if true
	if(*(char *)&n == 1)
		printf("little endian");
	else
		printf("big endian");
}
```

