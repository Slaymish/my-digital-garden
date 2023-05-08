---
{"dg-publish":true,"permalink":"/nwen-241/nwen-c-fundamentals/"}
---


# NWEN C Fundamentals

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

[[NWEN241/NWEN Run your code\|NWEN Run your code]] : C code run through gcc

## Identifiers

- Used to name macros, variables, fns, structs, unions etc
- Java and C have *similar* rules
- First character must be a letter
	- "_" counts as a letter
- Case-sensitive
- Can't have keyword as intentifier

**Examples of valid/invalid indentifiers:**

```C
counter // Valid
_Temp_var_2 // Valid
1myVariable // Invalid
$steps // Invalid
continue // Invalid
```

***

# Data Types

- Different datatypes are different sizes
- Only char is fixed (1 byte)
- Other types are machine dependent
- Can use sizeof() to find size of var

**Integral Types: *Can store integer values***
- char
- short (short int) 
- int 
- long (long int) 
- long long (long long int)

**Float types: *Can store floating-point values***
- float
- double 
- long double

- Integral types can be **signed** or **unsigned**
	- Default is signed
	- unsigned ints can not be negative and thus has a higher range of positive values that it can assume

```C
signed int var1;
unsigned int var2;
```

## Char Type

- Unsigned char
	- 0 to 255
- Signed char
	- -128 to 127
- Mean to hold one ASCII characters

# Constants and Literals

- Constants are fixed values that can't be changed at runtime
- Fixed values are called literals
- List of literals:
	- Integer 
	- Floating Point 
	- Character 
	- String 
	- Enumeration


***

<h3 align="center">
Anything stating with '#' is a pre-processor
</h3>

Declaring constants:

```C
const float PI = 3.14;
const int MAX = 12345;

// or

#define PI 3.14
#define MAX 1234
```

# Floating Point Literals

- Can be written in decimal form or exponential form
- Can use 'f' (float) or 'L' (long double) as suffix to set datatype
- Default (without suffix) is double

# Character Literals

- Enclosed in single quotes
- '\\t' Tab
- '\\n' New Line
- '\\r' Return

***

# Type Casting

- C perform automatic type casting
	- Called implicit type conversion
- Type casting will only drop the decimal
	- (Won't round)

```C
int i = 2;
double d = 2.5;

i = (int)d; // Explicit type casting

i = d; // Implicit type casting
```

# Operators

- Similar to [[Year 1/COMP102/Java Syntax\|Java Syntax]]
- C specific operators
	- * 
	- & (*Getting the memory address of a var*)
	- ->
- If both operands are ints, '/' will do integer division
	- Eg 5/2 = 2


**Condition in if-else, else-if, while-loop, for-loop and dowhile-loop** 
- In Java, the condition must be an expression that evaluates to boolean
- In C, the condition is an expression that evaluates to any type
- Considered true if expression evaluates to non-zero value, otherwise false

***

# Functions

- No classes like java
- Has to be declared prior to its invocation

```C
return_type function_name( parameter_list )
{
	body of the function
}
```

- If you want to put function below main, use a fn prototype
	- If just the header of fn

```C
return_type function_name(parameter_list);

int main(void)
{
	function_name(params);
}

return_type function_name( parameter_list )
{
	// rwodvbdvbuodabsvo
}
```

***

# Switch

```C
switch(pid){
	case -1:
		printf("geiigi");
	case -1:
		printf("geiigi");
	case -1:
		printf("geiigi");
	default:
		printf("gbriovbu");
}
```