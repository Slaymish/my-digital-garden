---
{"dg-publish":true,"permalink":"/swen-221/swen-assertions/"}
---

Related: #
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 21-03-2023
***

- Added in Java 1.4

Basic use

```java
assert <condition>;
assert <condition> : <message>;

assert x!=null
// If x is null and assertions enabled
```

# How to Enable Assertions

*May be disabled by default*

CLI:
- java -ea MyMainClass
- java -ea -jar MyExecutablejarFile

**Enable assertions for a package:**
- -ea:namePackage...
	- No space before the three dots


Assertions vs testing:
- assertEquals();
	- NOT an assertion

Runtime verification:
- Testing normally outside app
- Runs extra tests inside running code

Method contracts:
- everything method has one
	- if not explicit, any object accepted for params is ok
- explicit below

```java
int factorial(int n){
assert n>=0;
if(n<1){return 1;}
return n*factorial(n-1);
}
```

Pre/Post conditions:
- Checks at start/end (respectively) of method
- eg

```java
void methodName(...){
	assert precondition();
	try{
		// ...do smth...
	}
	finally{ assert postcondition(); }
}
```

<h2 align="center">

If code to encode logic is 1k lines, a min of 1k lines of test and 1k lines of assertions-related code

</h2>


**Why do this:**
- Cooperate with documentation
- Cooperate with private state
- Good for debugging
- Make library usage safer
- When a library is used in unacceptable way
	- AssertionError with an information error message



Programmatically enablling assertions:
- Only works in class stated in

```java
public class Main{
	public static void main(String[] a){
		ClassLoader.getSystemClassLoader()
			.setDefaultAssertionStatus(true);
		assert false:"Will it break?"; // no error
	}
}

class other{
	static void method(){
		assert false:"Or here?"; // error here!
	}
}
```

Old test that used to be need:
- Still found in some legacy code
- Junit now enables assertions automatically

```java
@test void assertsAreRunning(){
	try{ assert false:"AAAH";}
	catch(AssertionError ae){return;}
	fail("Assertions are disabled");
}
```

***

# Contracts

- Precondition
	- Blame the user of your code
	- Can be
		- Debugging/testing support
		- Active documentation
		- Can be an assert
		- can be a throw
- Postcondition


**Invariants:**
- Some property that holds for all the instances of a type
- eg

```java
record Positive(int x){ Positive{assert x>0;} }
record Even(int x) { Even{ assert x%==0; }}

record Person(String name, Postive age){
	//code here
}
```