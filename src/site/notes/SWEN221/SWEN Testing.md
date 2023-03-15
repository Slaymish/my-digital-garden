---
{"dg-home":false,"dg-publish":true,"permalink":"/swen-221/swen-testing/","dgPassFrontmatter":true}
---

Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 13-03-2023
***

# Automated testing
- input file -> program run -> output file
- A test is another program/script
- Can use *System.In* and *System.Out*
- Faster and more reliable than manual testing

### Regression testing:
- Running your automated tests everytime you change anything in the code

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


## JUnit
*Unit Testing Framework*

http://junit.sourceforge.net/
- Tests are java methods
- Test suites are Java classes
- Annotations mark them out
- API for writing tests
- Supports IDE's

### Your test class
```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;
```
##### assert** methods:
- assertTrue(bool)
- assertTrue(String msg, bool)
- **assertEquals(Object expect, Object actual)**
- assertEquals(float expect, float actual, float delta)
- assertNull, assertNotNull
- assertFalse
- assertSame, assertNotSame
- **assertThrows(Err.class,()->my)**
- fail(), fail(String msg)