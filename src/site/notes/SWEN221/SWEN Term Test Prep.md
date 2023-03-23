---
{"dg-home":false,"dg-publish":true,"permalink":"/swen-221/swen-term-test-prep/","dgPassFrontmatter":true}
---

Related: #java #programming #practise 
Contents: [[SWEN221/SWEN_MOC\|SWEN_MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN221_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 23-03-2023
***

## Mock Test Review

- Questions may contain information helpful for previous questions

### Q3: longestString

- Given a List<String> ss
- Can add own asserts: `assert myCondition: myMessage`
- Use `.length()` on Strings
- Alternative solution:

```java
return ss.stream()
    .max( (s1,s2)->Integer.compare(s1.length(),s2.length()) )
    .orElseThrow( IllegalArgumentException::new );
```

### Q6: Solution Skeleton

- Create a basic outline of the solution
- Divide into simple parts

### Q7: Return 'this'

- Part of the question: `assert a.b().zero() == 0`
- Instead of creating A *and* B classes, use return *this* for `b()` method
  - Only need an A class

### Q9: Using Non-imported Classes

- Can still use non-imported classes, e.g., ArrayList:

```java
new java.util.ArrayList<String>(ss) // Use the full name
```

- Applicable for any non-imported classes

## Term Test 1: Preparation

**Study documentation for:**

- [String](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/String.html)
- [Integer](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Integer.html)
- [List](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/util/List.html)
- [Set](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/util/Set.html)
- [Map](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/util/Map.html)

**Also, get familiar with:**

- Constructors for ArrayList, HashSet, HashMap
- Methods of Double, Float, Boolean

**Memorize:**

- Important methods and behavior for String, Integer, List, Set, Map

**Course content priority:**

- Content up to Assertions (10) on 20th March

**Test format:**

- 10 questions, similar in size to mock test





