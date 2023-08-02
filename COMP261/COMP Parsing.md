---
dg-home: false
dg-publish: true
---

# COMP Parsing

Related: #programming #java 
Contents: [[COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
Hamish Burke || 02-03-2023
***


COMP261 Focusing on these two:
- Text with markup
- Programs written in programming languages

## **Examples Of Formal languages:**

XML docs:

```XML
<html><head><title>My Web Page</title></head>
<body><p>Thanks for viewing</p></body></html>
```

Java Statements:

```java
while (A[k]!=x){if(k>0){A[k]+=A[k-1];} k++}
```

SQL schema defs or query:

```sql
DELETE FROM DomesticStudentsFor2022
WHERE mark = 'E';
```

***

### Grammar of HTML:

```html
HTMLFILE ::= "<html>" [ HEAD ] BODY "</html>"
BODY ::= "<body>" [BODYTAG]* "</body>"
BODYTAG ::= H1TAG | PTAG | OLTAG | ULTAG
H1TAG ::= "<h1>" TEXT "</h1>"
OLTAG ::= "<ol>" [LITAG]+ "</ol>"
```

Rules to understand those rules:
- '::=' = A grammar rule
- '|' = or
- '[...]' = optional
- '[...]\*' = Any number of times
- '[...]+' = one or more times

Nonterminals:
- Elements of the grammar
- Not the actual text

Terminals:
- The actual text displayed

***

### Using the Grammar:

```html
<html>
	<head><title>TITLE</title></head>
	<body>
		<h1>My day</h1>
		<ul><li>meeting</li><li>lecture</li></ul>
		<p> Parsing stuff</p>
	</body>
</html>
```

1. Is it a valid piece of HTML?
	- Does it conform to the grammar rules
2. What is the structure of the text?
	1. What are the components?
	2. What types are the components?
	3. How are they related?

What type of structure?
- Ordered tree
	- Order of children matter
- Each node and its children correspond to a grammar rule
- Each internal node labeled by the nonterminal on LHS of the rule
- Leaves correspond to terminals

![[SCR-20230302-nkn.png]]

***

# Abstract Syntax Tree (AST)

- Instead of a concrete parse tree
- Each node of the tree denontes some construct occurring in the text
![[SCR-20230302-no4.png]]

How to write a parser program?:
- [[COMP Lexical Analysis]]
- Parsing
	- Analysing the sequence of tokens

## Parsing Algorithms:

- Top-down vs bottom-up
- Assignment 1 requires you to write a **recursive descent parser**

### Top Down Recursive Descent Parser

- [More info here](COMP Recursive Descent Parsing)
- Starts with expression, then goes to more indepth
	- Mutually-recursive procedures
- Structure of the resulting program will closely mirror the grammar it recognizes
- Better than just looking at each token by itself


A 'naive' parser would look like:

```java
public boolean parseSENT(Scanner s){
	if(s.hasNext("the")) {
		s.next(); return parseDEFNP(s);
	}
	else if (s.hasNext("a")) {
		s.next(); return parseINDEFNP(s);
	}
	else { 
		return false;
	}
}
```

## Using the Scanner:

- Use scanner with delimiter

```java
public void parse(String input) {
	Scanner s = new Scanner(input);
	s.useDelimiter("\\s*(?=[(),])|(?<=[(),])\\s*");
	if(parseExpr(s)){
		System.out.println("Thats a valid expr");
	}
}
```

```java
s.hasNext("add")
s.hasNext("[-+]?[0-9]+") // can put regular exprs
```

- Parsing exprs (checking only)

```java
public boolean parseAdd(Scanner s) {
	if(s.hasNext("add")){s.next();} else {return false;}
	if(s.hasNext("(")){s.next();} else {return false;}
	if(parseExpr(s){} else {return false;}
	//etc etc
}
```