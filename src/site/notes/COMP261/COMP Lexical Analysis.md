---
{"dg-publish":true,"permalink":"/comp-261/comp-lexical-analysis/"}
---


# COMP Lexical Analysis

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-03-2023
***

- Need to separate the text into a sequence of tokens
	- Java scanner, by default, separates at white space
		- Not what we want!

## Use a 'Regular Expression'

*java.util.regexp.Pattern*
- String with 'wild cards'
- [-+\*/] : sets of possible characters
- | : specifying alternatives
- \* + ? : specifying repetitions
- (?<=before) (?=after) : specifying pre-context and post-context

eg:

```java
// these find tokens that match this pattern

scan.useDelimiter("\\s*(?=[<])|(?<=[>])\\s*") // works well with html!
scan.useDelimiter("\\s+|(?=[{}(),;])|(?<=[{}(),;])") // good for java (also for assgn 1)
```

### Tools Used to Do This IRL

- LEX, JFLEX, ANTLR etc

***

**Alternative approach:**
- Define a pattern matching the tokens
	- *instead of a pattern matching the separators between tokens*
- Make a method that will search for and return the next token



