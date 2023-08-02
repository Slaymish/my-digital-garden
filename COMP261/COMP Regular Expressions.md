---
dg-home: false
dg-publish: true
---
Related: #programming #java 
Contents: [[COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 14-03-2023
***

# LL(1) Grammars:

- Single look-ahead
- Type of context-free grammar
- Easy to make more complex grammars/languages

# Regular Grammars

^85c3b3

*Simpler grammar*
- Easier to parse 
- Equivalent to finite state automata. 
- Equivalent to regular expressions

## [[COMP Lexical Analysis]]

*Using a regular expression*

- Java scanner can use regular expression patterns to separate the tokens

```java
scan.useDelimiter("\\s*(?=[<])|(?<=[>])\\s");
scan.useDelimiter("\\s+|({}(),;)|(?<=[{}(),;])");
```

## Language of Regular Expressions

^00f123

- $15$
	- Matches only itself
- $[1-9][0-9]$
	- [...] = contains a set of character
	- - = is a range
	- match 10, 82 not 03, or 4
- $tes+t:?\ [1-9][0-9]*$
	- \+ = 1 or more repetitions
	- \* = 0 or more repetitions
	- \? = 0 or 1 repetitions (optional)
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
\[^....\] = matches any character **except** whats in the [....]
\\d, \\s, \\w, \\W = abbreviations for common [...]: digit, space, word char, non-word char
^ $ = match the boundary between chars at beginner or end of a line
\\b = match the boundary between a word and non-word (either side)
\\ = makes special characters ordinary (may need double \\ \\ )
