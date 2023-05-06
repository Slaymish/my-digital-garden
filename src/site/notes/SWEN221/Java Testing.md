---
{"dg-publish":true,"permalink":"/swen-221/java-testing/"}
---

Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 13-03-2023
***

# Automated Testing

- input file -> program run -> output file
- A test is another program/script
- Can use *System.In* and *System.Out*
- Faster and more reliable than manual testing

## Regression Testing:

- Running your automated tests every time you change anything in the code

***

<h1 align="center">
Fail Faster my friend... Fail Faster!
</h1>

***

# Unit Testing

- Tests each method in code individually
- Create input
- Call method
- Check result

***

## JUnit

*Unit Testing Framework*

<http://junit.sourceforge.net/>
- Tests are java methods
- Test suites are Java classes
- Annotations mark them out
- API for writing tests
- Supports IDE's

### Your Test Class

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;
```

#### assert** Methods:

- assertTrue(bool)
- assertTrue(String msg, bool)
- **assertEquals(Object expect, Object actual)**
- assertEquals(float expect, float actual, float delta)
- assertNull, assertNotNull
- assertFalse
- assertSame, assertNotSame
- **assertThrows(Err.class,()->my)**
- fail(), fail(String msg)

***

## Example

Base code:

```java
record MyDate(int day, int month, int year){
	public MyDate{
		if(day <= 0 || month < 0){throw new RuntimeException(/**/);}
		if(day > 31 || month > 12){throw new RuntimeException(/**/);}
		...
		
	}

	private static boolean isLeapYear(int year){
		...
	}
}
```

A simple JUnit test

## Testing the Happy Path

```java
public class MyDateTest{
	@Test public void testConstructValidDate(){
		new MyDate(1,1,1);
		new MyDate(1,5,2006);
		new MyDate(28,5,2004);
		new MyDate(4,3,2004);
	}
}
```

## Testing the Unhappy Path

```java
@Test public void testConstructInvalidDate(){
	assertThrows(re, ()->new MyDate(0,0,0) );
	assertThrows(re, ()->new MyDate(29,2,2006) );
	assertThrows(re, ()->new MyDate(31,6,2006) );
	assertThrows(re, ()->new MyDate(11,1,-1) );
}
```

***

# How Does JUnit Work

- The main method is inside the Junit library
- Receives the name of the test class/classes in input
- Their old main class runs our code
	- [[SWEN221/Java Time Travelling\|time travelling]]!

**Code is testable if:**
- Easy to create objects to run
- Easy to run operations
- Easy to check the result of the operations

## Property Testing

- Generate some input and check general properties