---
{"dg-home":false,"dg-publish":true,"permalink":"/comp-261/comp-regular-expressions/","dgPassFrontmatter":true}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 14-03-2023
***
## LL(1) grammars: 
- Single look-ahead
- Type of context-free grammar
- Easy to make more complex grammars/languages

# Regular Grammars
*Simpler grammer*
- Easier to parse 
- Equivalent to finite state automata. 
- Equivalent to regular expressions

## [[COMP261/COMP Lexical Analysis\|COMP Lexical Analysis]]
*Using a regular expression*

- Java scanner can use regular expression patterns to separate the tokens
```java
scan.useDelimiter("\\s*(?=[<])|(?<=[>])\\s");
scan.useDelimiter("\\s+|({}(),;)|(?<=[{}(),;])");
```



## Language of Regualar Expressions
- $15$
	- Matches only itself
- $[1-9][0-9]$
	- [...] = contains a set of character
	- - = is a range
	- match 10, 82 not 03, or 4
- $tes+t:?\ [1-9][0-9]*$
	- + = 1 or more repetitions
	- * = 0 or more repetitions
	- ? = 0 or 1 repetitions (optional)
	- match
		- test: 34
		- tesst 29
		- tessssst: 250002
- $(pat\ )+(dog|cat)$
	- | = or
	- matches pat dog or pat pat pat cat


<h2 align="center">

Syntax: [ ] ( ) | * + ?

</h2>
<p align="center">
These are sufficient for everything
</p>


## Extensions
*X{n,m}* = X, at least n but not more than m times
*X{n} X{n,}* = X, exactly n time, or at least n times