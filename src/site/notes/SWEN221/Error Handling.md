---
{"dg-publish":true,"permalink":"/swen-221/error-handling/"}
---

Related: #
Contents: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
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

## Difference between Throwing and Returning:

-   return:
    -   Exits a method
    -   Returns a value to the calling method
    -   Does not indicate an error or exception
-   throw:
    -   Signals an exception/error
    -   Requires an exception object
    -   Can be caught by a try-catch block
    -   Interrupts normal program flow

## Try-Catch Block

- 'Catches' exception that have been thrown
- Makes it so you can continue runtime

## Nesting exception

- getCause()
- getMessage()
- getStackTrace()
- Exceptions are a **language** feature

# Finally Clause

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

# Don't Overpower the Hero

*Handle* exceptions instead of just catching them


***

# Exception with |

```java
void foo() {
	try{ bar(); }
	catch( RuntimeException | Error unchecked ){
		// here 'uncheck is either of type
		// 'RuntimeException' or 'Error'
	}
}
```

