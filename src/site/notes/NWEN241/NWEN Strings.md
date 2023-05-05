---
{"dg-publish":true,"permalink":"/nwen-241/nwen-strings/"}
---


# NWEN Strings

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

## Whats a String in C?

- A C string a just an array that contains ASCII characters
	- its a char array ([[NWEN241/NWEN_Arrays\|NWEN_Arrays]])
	- Need null char to make it a valid string

## Null Character in Strings

- Dont count null char in string length
	- Terminated by the null character '\0'
	- use strlen() to get string length

### String Literal

- Constant value
- Can be subscripted!
	- ie `"hello"[2] //returns 'l'`
- Stored in read-only memory area
- **Enclosed in double quotes**
- Use \ at end of lines to do multiline

```C
"A" // Literal - contains 2 chars (A and null terminator)
'A' // Character constant
```

- Passed to functions as [*pointers*](NWEN Pointers) to a stored string

### String Variable

- A string that is stored in an array which can be modified
- Terminated by the null char
- Can be initialize in multiple ways

```C
char str[10];
str[0] = 'H';
str[1] = 'e';
...
//or
char str[10] = {'H', 'e', 'l', 'l', 'o', ' ', '!', '\0' };
// or (actual way)
char str[] = "Hello World!"; 
```

### Assigning a String after Array Declaration

```C
char str[10];
str = "Hello !"; // Illegal! Use strcpy() function 

char str[10];
strcpy(str, "Hello !");
```

### <ctype.h> Header

- Declares a set of fns to classify/transform indivigual chars
- eg
	- isupper()
	- islower()
	- toupper()
	- tolower()

### <string.h> Header

- strcpy()
	- copies string from src to dest
- strcat()
	- concatenates two strings
- etc

### <stdlib.h> Header

- fns to search, sort and convert
- eg
	- atoi()
	- atof()
	- atol()
- Parses a string of chars into a number of type int, double, float, long etc



