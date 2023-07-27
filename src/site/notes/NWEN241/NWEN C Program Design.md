---
{"dg-publish":true,"permalink":"/nwen-241/nwen-c-program-design/"}
---


# NWEN C Program Design

Related: #programming #C 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
Hamish Burke || 27-02-2023
***

```C
#include <stdio.h>

int main(void)
{
	printf("hello world\n");
	return 0;
}
```

**Notes about structure:**
- printf is from stdio.h
- must have main fn
	- int main(void)

**Header File Inclusion:**
- Using <>
	- Preprocessor searches for file in pre-defined locations
- Using ""
	- Preprocessor searches for file in current directory first, then in locations specified by programmer

**Large C Program**:
- Will have
	- Pre-installed header files
	- Own Header files
	- .c Source Files
