---
dg-home: false
dg-publish: false
---
Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 01-04-2023
***

# Q1

i) 

```
8 bit grey code = range from 00000000 to 11111111
256 unique codes
Angular res = 360/256 = 1.40625 degrees
```

ii)

```
Grey code = 01101101 // First bit same, xor with right diag, left to right

Binary: 01001001

test:
11111111
10101010

```

iii)

```
Starts at 00000000
Angular position when 01101101 (grey code)

01101101
01001001 - 73 in binary

1.40625 (angular res) * 73 = 102.65625 degrees from start


```

iv)

```
As I don't know the circumfrince of the rotary wheel, I'm unable to determine how large each step is, in relation to the circle. It could range from 102.65625 to 104.0625. This is because each step isn't infinatly small, because it takes up physically space on the wheel. 
```

v)

```
01001001 - 73 in binary
```

# Q2

```
Mod 10
4 Bits - BCD output

Never higher than 1001 (9)

```

| Count | A   | B   | C   | D   | X   |
| ----- | --- | --- | --- | --- | --- |
| 0     | 0   | 0   | 0   | 0   |     |
| 1     | 0   | 0   | 0   | 1   |     |
| 2     | 0   | 0   | 1   | 0   |   $\neg A \neg B C \neg D$  |
| 3     | 0   | 0   | 1   | 1   |   $\neg A \neg B C D$  |
| 4     | 0   | 1   | 0   | 0   |     |
| 5     | 0   | 1   | 0   | 1   |     |
| 6     | 0   | 1   | 1   | 0   |     |
| 7     | 0   | 1   | 1   | 1   |     |
| 8     | 1   | 0   | 0   | 0   |     |
| 9     | 1   | 0   | 0   | 1   | $A \neg B \neg C D$    |
| 10    | 0   | 0   | 0   | 0    |     |

 $$(\neg A \neg B C \neg D) + (\neg A \neg B C D) + (A \neg B \neg C D)$$

*X = don't care states*

|       | $AB$ | $A \neg B$ | $\neg A B$ | $\neg A \neg B$ |
| ----- | ---- | ------ | ----- | ------ |
| $CD$    |  X    |   X    |        |  1      |
| $C \neg D$   |  X    |   X     |       |    1     |
| $\neg C D$   |   X   |     1   |        |         |
| $\neg C \neg D$  |    X  |        |        |         |

![[SCR-20230411-u8o.png]]

Map layout:

![[SCR-20230411-u91.png]]

Groups:

![[SCR-20230411-u9b.png]]


Simplified equation:
$y = \neg BC + AD$

Logic Circuit:

![[Diagram 23.svg]]

# Q3

| SW1 | SW2 | SW3 | SW4 | X   |
| --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | 0   |
| 0   | 0   | 0   | 1   |  0   |
| 0   | 0   | 1   | 0   |   0  |
| 0   | 0   | 1   | 1   |   1  |
| 0   | 1   | 0   | 0   |    0 |
| 0   | 1   | 0   | 1   |     1|
| 0   | 1   | 1   | 0   |  1   |
| 0   | 1   | 1   | 1   |   1  |
| 1   | 0   | 0   | 0   |    0 |
| 1   | 0   | 0   | 1   | X   |
| 1   | 0   | 1   | 0   | 1    |
| 1   | 0   | 1   | 1   | X   |
| 1   | 1   | 0   | 0   |    1 |
| 1   | 1   | 0   | 1   | X   |
| 1   | 1   | 1   | 0   |   1  |
| 1   | 1   | 1   | 1   | X   |

|                 | $\neg C \neg D$ | $\neg CD$ | CD  | $C \neg D$ |
| --------------- | --------------- | --------- | --- | ---------- |
| $\neg A \neg B$ | 0               | 0         | 1   | 0          |
| $\neg A B$      | 0               | 1         | 1   | 1          |
| $AB$            | 1               | X         | X   | 1          |
| $A \neg B$      | 0               | X         | X   | 1           |

$X = CD + BD + BC + AC + AB$

![[SCR-20230405-tpz.png]]

# Q4

![[SCR-20230405-u77.png]]

# Q5

- $18 kHz / 1.2 kHz = 15$
- Trying to make a counter that divides by 15 (mod 15)
- On 15th state, reset counter

$15 = 2^n$
$n= 3.9$
Number of FF $= 4$

## I. Logic Diagram

![[SCR-20230405-vd7.png]]

## Ii. Circuit Diagram with 74HCT112 JK FF ICs

![[SCR-20230405-vcu.png]]

# Q6

```
Same state transition diagram as JK FF implementation
```

| Present Q | Next Q | D   |
| --------- | ------ | --- |
| 0         | 0      | 0   |
| 0         | 1      | 1   |
| 1         | 0      | 0   |
| 1         | 1      | 1    |

| D   |     | Q2  | Q1  | Q0  |     | Q2+ | Q1+ | Q0+ |     | D2  | D1  | D0  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   |     | 0   | 0   | 0   |     | 0   | 1   | 0   |     | 0   | 1   | 0   |
| 0   |     | 0   | 0   | 1   |     | 0   | 0   | 0   |     | 0   | 0   | 0   |
| 0   |     | 0   | 1   | 0   |     | 1   | 0   | 0   |     | 1   | 0   | 0   |
| 0   |     | 0   | 1   | 1   |     | 0   | 0   | 0   |     | 0   | 0   | 0   |
| 0   |     | 1   | 0   | 0   |     | 1   | 1   | 0   |     | 1   | 1   | 0   |
| 0   |     | 1   | 0   | 1   |     | 0   | 0   | 0   |     | 0   | 0   | 0   |
| 0   |     | 1   | 1   | 0   |     | 0   | 0   | 0   |     | 0   | 0   | 0   |
| 0   |     | 1   | 1   | 1   |     | 0   | 0   | 0   |     | 0   | 0   | 0   |
| 1   |     | 0   | 0   | 0   |     | 0   | 0   | 1   |     | 0   | 0   | 1   |
| 1   |     | 0   | 0   | 1   |     | 0   | 1   | 1   |     | 0   | 1   | 1   |
| 1   |     | 0   | 1   | 0   |     | 0   | 0   | 1   |     | 0   | 0   | 1   |
| 1   |     | 0   | 1   | 1   |     | 1   | 0   | 1   |     | 1   | 0   | 1   |
| 1   |     | 1   | 0   | 0   |     | 0   | 0   | 1   |     | 0   | 0   | 1   |
| 1   |     | 1   | 0   | 1   |     | 1   | 1   | 1   |     | 1   | 1   | 1   |
| 1   |     | 1   | 1   | 0   |     | 0   | 0   | 1   |     | 0   | 0   | 1   |
| 1   |     | 1   | 1   | 1   |     | 0   | 0   | 1   |     | 0   | 0   | 1   |

## $D_2$:

|                   | $\neg Q_1 \neg Q_0$ | $\neg Q_1 Q_0$ | $Q_1 Q_0$ | $Q_1 \neg Q_0$ |
| ----------------- | ------------------- | -------------- | --------- | -------------- |
| $\neg D \neg Q_2$ | 0                   | 0              | 0         | 1              |
| $\neg D Q_2$      | 1                   | 0              | 0         | 0              |
| $D Q_2$           | 0                   | 1              | 0         | 0               |
| $D \neg Q_2$      | 0                   |       0         | 1         |     0           |

$D_2 = D'Q2'Q1Q0' + D'Q2Q1'Q0' + DQ2'Q1Q0 + DQ2Q1'Q0$

$D_2 = (\neg D \neg Q_2 Q_1 \neg Q_0) + (\neg D Q_2 \neg Q_1 \neg Q_0) + (D \neg Q_2 Q_1 Q_0) + (D Q_2 \neg Q_1 Q_0)$

$$D_2 = \neg D Q_1 + D Q_0$$

## $D_1$:

|                   | $\neg Q_1 \neg Q_0$ | $\neg Q_1 Q_0$ | $Q_1 Q_0$ | $Q_1 \neg Q_0$ |
| ----------------- | ------------------- | -------------- | --------- | -------------- |
| $\neg D \neg Q_2$ | 1                  | 0              | 0         | 0              |
| $\neg D Q_2$      | 1                   | 0              | 0         | 0              |
| $D Q_2$           | 0                   | 1              | 0         | 0               |
| $D \neg Q_2$      | 0                   |       1         | 0         |     0           |

$= \neg D Q_2 \neg Q_1 + D Q_2 \neg Q_1 \neg Q_0$.
$= \neg Q_1 (\neg D Q_2 + D Q_2 \neg Q_0)$
$= \neg Q_1 Q_2 (\neg D + D \neg Q_0)$
$= \neg Q_1 Q_2 \neg Q_0$

$$D_1 = \neg Q_1 Q_2 \neg Q_0$$

## $D_0$:

$$D_0 = D$$

### Using Logic Gates:

1.  D_2: requires 2 AND gates, 1 OR gate, and 1 NOT gate.
2.  D_1: requires 3 AND gates and 1 NOT gate.
3.  D_0: no additional gates needed since it is directly connected to D.

Total logic gates: 6 AND gates, 1 OR gate, and 2 NOT gates.

### Using MUXes:

1.  D_2: can be implemented with a 2:1 MUX, with D as the selector input, Q_0 as input 0, and Q_1 as input 1.
2.  D_1: can be implemented with a 4:1 MUX, with Q_1Q_0 as the selector inputs. The inputs will be:
    -   Input 0 (00): 0
    -   Input 1 (01): ¬Q_2
    -   Input 2 (10): 0
    -   Input 3 (11): 0
3.  D_0: no additional MUX needed since it is directly connected to D.

Total MUXes: 1 2:1 MUX and 1 4:1 MUX. Note that the 4:1 MUX can be implemented with two 2:1 MUXes and one OR gate.

The implementation using logic gates requires more components: 6 AND gates, 1 OR gate, and 2 NOT gates. In contrast, the implementation using MUXes only needs 1 2:1 MUX and 1 4:1 MUX (or two 2:1 MUXes and one OR gate). 

Therefore, using MUXes would produce a simpler implementation due to the reduced number of components.

# Q7

- 3 bit
- 3 JK FF's

| $Q_1$ | $Q_2$ | $Q_3$ |
| ----- | ----- | ----- |
| 0     | 0     | 0     |
| 0     | 1     | 0     |
| 1     | 0     | 1     |
| 1     | 1     | 0     |

1.  For Q0 (LSB):
	-   $J_0 = Q_1'Q_2'$
	-   $K_0 = Q_1'Q_2'$

2.  For Q1:
	-   $J_1 = Q_0Q_2$
	-   $K_1 = Q_0'Q_2'$

3.  For Q2 (MSB):
	-   $J_2 = Q_0Q_1$
	-   $K_2 = Q_0'Q_1' + Q_0Q_1'$


![[Diagram 26.svg]]

# Q8

```
This simplified design ignores the behavior of the undesired states and focuses on the required sequence. The J-K flip flop inputs are simpler compared to the previous design, which accounted for the undesired states transitioning to 000.
```

![[Diagram 27.svg]]

