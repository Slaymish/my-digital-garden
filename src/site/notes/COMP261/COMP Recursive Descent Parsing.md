---
{"dg-publish":true,"permalink":"/comp-261/comp-recursive-descent-parsing/"}
---


# COMP Recursive Descent Parsing

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 10-03-2023
***

## Properties

- Works on LL(1) grammars
	- Top down
- Is deterministic
- One-token lookahead
	- Bases choice on next token only
- left to right


- Issue is can't read multiple lines ahead
- To fix look below
![SCR-20230310-kks.png](/img/user/SCR-20230310-kks.png)

***

## Ambiguous Grammars

- LIST ::= id | LIST "," LIST
	- could be just a value
	- or could be two, separated by a comma

Fix it by changing rule:
- LIST ::= id | LIST "," id

Force right recursion
- LIST ::= id | id "," LIST

Can **factor** it:
- LIST ::= id RESTLIST
- RESTLIST ::= "," LIST | ""


<h3 align="center">
Left recursion:
</h3>
<p align="center">
E ::= number | E + num | E * num | E - num
</p>

***


<h3 align="center">
Right recursion:
</h3>
<p align="center">
E ::= number | num + E | num * E | num - E
</p>















