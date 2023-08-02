---
dg-home: true
dg-publish: true
---

# Hamish's Notes

[[Plan\|Todays Plan]]

## Lastest Notes

[[NWEN241 MOC|NWEN241]]
- [[NWEN System Calls]]
- [[NWEN Processes]]
- [[NWEN Interprocess Communication]]
- [[NWEN Sockets]]
- [[NWEN Host and network byte order]]
- [[Process Initialisation on Linux]]
- [[Intro to C++]]

[[EEEN202 MOC|EEEN202]]
- [[EEEN Asynchronous Counters]]
- [[EEEN Design Report]]
- [[EEEN Synchronous Counters]]
- [[Microprocessors]]
- [[Program Status Word]]
- [[The 8051 Instruction Set]]
- [[EEEN Design Report]]

[[COMP261 MOC|COMP261]]
- [[COMP Regular Expressions\|Regular Expressions]]
- [[COMP FSA Acceptors\|FSA Acceptors]]
- [[COMP Test Prep]]
- [[StringBuilder]]
- [[COMP Graphs and data structures]]

[[SWEN221 MOC|SWEN221]]
- [[SWEN Garbage Collection]]
- [[SWEN Reflection]]
- [[SWEN Recent Pattern Syntax]]
- [[SWEN Var args syntax]]
- [[Types of Programming]]
- [[SWEN Term Test 3 Prep]]
- [[SWEN Stream Method]]
- [[Minecraft Bug - If statements]]
- [[Java Streams]]


[[SWEN225 MOC]]
[[NWEN243 MOC]]
[[CGRA251 MOC]]
[[CYBR271 MOC]]



***

## Code Examples

```java
public static <T extends Shape> T tallestShape(List<T> shapes){
	return shapes.stream()
		.max(Comparator.comparing(shapes::height))
		.orElseThrow(() -> new IllegalArgumentException());
}
```

```C
#include <stdio.h>
int main(void)
{
	printf("Hello Wrold!");
	return 0;
}
```

```C++
#include <cstdio>
int main(void)
{
	std::cout<<"Hello World";
	return 0;
}
```

```assembly
MOV A,R1
ACALL INCR
MOV R1,A

MOV A,R2
ACALL INCR
MOV R2,A


INCR:
	ADD A,#1
	RET
```

***

[[Contact]] me!

