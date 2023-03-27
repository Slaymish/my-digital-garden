---
{"dg-home":false,"dg-publish":true,"permalink":"/eeen-synchronous-counters/","dgPassFrontmatter":true}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-03-2023
***

- Can either use JK or D flip-flops


## Excitation table for J-K FF

| Present Q | Next Q | J   | K   |
| --------- | ------ | --- | --- |
| 0         | 0      | 0   | x   |
| 0         | 1      | 1   | x   |
| 1         | 0      | x   | 1   |
| 1         | 1      | x   | 0    |


## Excitation table for D FF

| Present Q | Next Q | Input D |
| --------- | ------ | ------- |
| 0         | 0      | 0       |
| 0         | 1      | 1       |
| 1         | 0      | 0       |
| 1         | 1      | 1       |



***

## Synchronous Example Counter
*Using JK FF that'll count the first eight binary states*

- Write down the counting sequence

$$000 \implies 001 \implies 010 \implies 011 \implies 100 \implies 101 \implies 110 \implies 111 \implies 000$$


This is MOD eight, this 3 FF's [^1]


- Draw the state transition diagram, showing all state including the undesired state


![300](https://femboy.beauty/tCUg1)


- Draw up a table that lists all **present** state and their **next** states

- Design logic circuits needed to generate the levels required at each J and K input
	- Use K-map for simplification 






[^1]: [[EEEN202/EEEN Asynchronous Counters#^6c61c8\|Formula here]]