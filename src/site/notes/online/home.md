---
{"dg-publish":true,"permalink":"/online/home/","tags":["gardenEntry"]}
---


# Hamish's Notes

[[Plan\|Todays Plan]]

## Lastest Notes

[[NWEN241/NWEN MOC\|NWEN241]]
- [[NWEN System Calls\|NWEN System Calls]]
- [[NWEN Processes\|NWEN Processes]]
- [[NWEN Interprocess Communication\|NWEN Interprocess Communication]]
- [[NWEN Sockets\|NWEN Sockets]]
- [[NWEN Host and network byte order\|NWEN Host and network byte order]]
- [[Process Initialisation on Linux\|Process Initialisation on Linux]]
- [[Intro to C++\|Intro to C++]]

[[EEEN202/EEEN MOC\|EEEN202]]
- [[EEEN202/EEEN Asynchronous Counters\|EEEN Asynchronous Counters]]
- [[EEEN Design Report\|EEEN Design Report]]
- [[EEEN Synchronous Counters\|EEEN Synchronous Counters]]
- [[Microprocessors\|Microprocessors]]
- [[Program Status Word\|Program Status Word]]
- [[The 8051 Instruction Set\|The 8051 Instruction Set]]
- [[EEEN Design Report\|EEEN Design Report]]

[[COMP261/COMP MOC\|COMP261]]
- [[COMP261/COMP Regular Expressions\|Regular Expressions]]
- [[COMP FSA Acceptors\|FSA Acceptors]]
- [[COMP261/COMP Test Prep\|COMP Test Prep]]
- [[StringBuilder\|StringBuilder]]
- [[COMP Graphs and data structures\|COMP Graphs and data structures]]

[[SWEN221/SWEN_MOC\|SWEN221]]
- [[SWEN Garbage Collection\|SWEN Garbage Collection]]
- [[SWEN Reflection\|SWEN Reflection]]
- [[SWEN Recent Pattern Syntax\|SWEN Recent Pattern Syntax]]
- [[SWEN Var args syntax\|SWEN Var args syntax]]
- [[Types of Programming\|Types of Programming]]
- [[SWEN Term Test 3 Prep\|SWEN Term Test 3 Prep]]
- [[SWEN Stream Method\|SWEN Stream Method]]
- [[Minecraft Bug - If statements\|Minecraft Bug - If statements]]
- [[Java Streams\|Java Streams]]

***

## Code Examples

o```java
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

[[Contact\|Contact]] me!

