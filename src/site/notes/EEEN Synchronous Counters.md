---
{"dg-publish":true,"permalink":"/eeen-synchronous-counters/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-03-2023
***

- Can either use JK or D flip-flops

# Excitation Table for J-K FF

| Present Q | Next Q | J   | K   |
| --------- | ------ | --- | --- |
| 0         | 0      | 0   | x   |
| 0         | 1      | 1   | x   |
| 1         | 0      | x   | 1   |
| 1         | 1      | x   | 0    |

# Excitation Table for D FF

| Present Q | Next Q | Input D |
| --------- | ------ | ------- |
| 0         | 0      | 0       |
| 0         | 1      | 1       |
| 1         | 0      | 0       |
| 1         | 1      | 1       |

***

# Synchronous Example Counter

*Using JK FF that'll count the first eight binary states*

- Write down the counting sequence

$$000 \implies 001 \implies 010 \implies 011 \implies 100 \implies 101 \implies 110 \implies 111 \implies 000$$


This is MOD eight, this 3 FF's [^1]


- Draw the state transition diagram, showing all state including the undesired state


![300](https://femboy.beauty/tCUg1)


- Draw up a table that lists all **present** state and their **next** states

- Design logic circuits needed to generate the levels required at each J and K input
	- Use K-map for simplification 


***

# Examples of Synchronous Counters

**Will be in test!**

Control input -> combinatorial logic elements -> sequential logic elements (clk in) -->> out and back into combinatorial logic elements

## 3 Bit Synchronous counter
{ #6d563d}


Going through states:
- 000
- 001
- 011
- 010
- 110
- 100
- 000

- **Use D FF's**

### Steps:

1. Determine counting sequence and desired num of bits (FF's) needed
	1. MOD 6, thus 3FF's but with two undesired states
2. Draw state transition diagram
	1. Shows all state (including undesired)
	2. If an undesired state happens, it should go to 000 on next count
3. Draw [[Excitation table for D FF counter\|excitation table]]
	1. Write present state in normal binary order (000,001 etc)
4. Design logic circuits
	1. [[EEEN202/EEEN K Maps\|Create K Maps]]
		1. Relate to input params
		2. 3 inputs = 3 K-maps
		3. $D_2=Q_1 \neg Q_0$ 
		4. $D_1=\neg Q_2 Q_1 + \neg Q_2 Q_0$ 
		5. $D_0 = \neg Q_2 \neg Q_1$
	2. Use results of K maps to create the logic
	3. OR use a MUX
		1. Use excitation table
		2. Will need 3 MUXes


***

## For Lab

- use a latch for the stop signal

[^1]: [[EEEN202/EEEN Asynchronous Counters#^6c61c8\|Formula here]]