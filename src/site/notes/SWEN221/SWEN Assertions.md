---
{"dg-home":false,"dg-publish":true,"permalink":"/swen-221/swen-assertions/","dgPassFrontmatter":true}
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

# How to enable assertions
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
- Checks at start/end (respectivley) of method
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



