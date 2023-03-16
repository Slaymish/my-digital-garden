---
{"dg-home":false,"dg-publish":true,"permalink":"/swen-221/swen-error-handling/","dgPassFrontmatter":true}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-03-2023
***
# Wrong way
```java
public static int factorial(int n){
	if(n < 0) {return -1;}
	if(n = 0) {return 1; }
	return n*factorial(n-1);
}
```
- Doesn't handle exceptions
- Relies on user to input correct values

***

# Exceptions
- Better way of dealing with errors is by *throwing* an exception

## Difference between throwing and returning:
-   return:
    -   Exits a method
    -   Returns a value to the calling method
    -   Does not indicate an error or exception
-   throw:
    -   Signals an exception/error
    -   Requires an exception object
    -   Can be caught by a try-catch block
    -   Interrupts normal program flow


## Try-Catch block
- 'Catches' exception that have been thrown
- Makes it so you can continue runtime


## Nesting exception
- getCause()
- getMessage()
- getStackTrace()
- Exceptions are a **language** feature


# Finally clause
- Gets in the last word, even after an exception is thrown
- Eg closing a file
```java
try { 
	int result = 10 / 2; 
	System.out.println("Result: " + result); 
	} 
catch (ArithmeticException e) { 
	System.out.println("Caught ArithmeticException: " + e.getMessage()); 
	} 
finally { 
	System.out.println("This will always execute, regardless of whether an exception occurred or not."); }
```


