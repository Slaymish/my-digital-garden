---
dg-home: false
dg-publish: true
---
Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 26-04-2023
***

# Combinatorial Logic

# 1.

a) 
![[Diagram 28.svg]]

b)
![[Diagram 29.svg]]

c)
![[Diagram 30.svg]]

# 2.

$$X=\neg (\neg (A+B) * \neg (B+\neg C))$$


| A   | B   | C   | $J = \neg (B + \neg C)$       | $I = \neg (A+B)$    | $X = \neg (J*I)$ | 
| --- | --- | --- | ----------------- | ------------  | --- |
| 0   | 0   | 0   |     0             |       1       |  1   |
| 0   | 0   | 1   |     1             |     1         |  0   |
| 0   | 1   | 0   |     0             |       0       |   1  |
| 0   | 1   | 1   |     0             |      0        |    1 |
| 1   | 0   | 0   |     0             |      0        |  1   |
| 1   | 0   | 1   |     1             |     0         |   1  |
| 1   | 1   | 0   |     0             |      0        |    1 |
| 1   | 1   | 1   |     0             |      0        |    1 |

![[Diagram 31.svg]]

# 3. Simplify with De Morgan's

De Morgan's Theorem: 
$\neg (AB) = \neg A + \neg B$



a)
$\neg (AB \neg (CD))$
$\neg (AB) + (CD)$


b)
$\neg (\neg A + \neg C + \neg D )$
$\neg (\neg A + \neg C )* D$ 
$A \cdot C \cdot D$


c)
$\neg ((M+ \neg N )(\neg M + N))$
$\neg (M+\neg N) + \neg (\neg M + N)$
$(\neg M \cdot N) + (M \cdot \neg N)$

# 4.

$X = (\neg A \cdot B) + (\neg B \cdot \neg C) + \neg D + E$

active at all states except:
- $\neg A \cdot \neg B \cdot C \cdot D \cdot \neg E$
- $A \cdot \neg B \cdot C \cdot D \cdot \neg E$
- $A \cdot B \cdot \neg C \cdot D \cdot \neg E$
- $A \cdot B \cdot C \cdot D \cdot \neg E$

| A   | B   | C   | D   | E   | $(\neg A \cdot B)$              | $(\neg B \cdot \neg C)$                | $\neg D$      | E   | X   |
| --- | --- | --- | --- | --- | :------------------: | :-----------------------: | -------- | --- | --- |
| 0   | 0   | 0   | 0   | 0   |                    |        1               |    1      |     |   1  |
| 0   | 0   | 0   | 0   | 1   |                    |   1                      |     1     |  1   |  1   |
| 0   | 0   | 0   | 1   | 0   |                    |    1                     |          |     |    1 |
| 0   | 0   | 0   | 1   | 1   |                    |     1                    |          |  1   |  1   |
| 0   | 0   | 1   | 0   | 0   |                    |                         |   1       |     |   1  |
| 0   | 0   | 1   | 0   | 1   |                    |                         |    1      |   1  |   1  |
| 0   | 0   | 1   | 1   | 0   |                    |                         |          |     |    ==0== |
| 0   | 0   | 1   | 1   | 1   |                    |                         |          |   1  |   1  |
| 0   | 1   | 0   | 0   | 0   |        1            |                         |   1       |     |  1   |
| 0   | 1   | 0   | 0   | 1   |        1            |                         |    1      |  1   |  1   |
| 0   | 1   | 0   | 1   | 0   |         1           |                         |          |     |    1 |
| 0   | 1   | 0   | 1   | 1   |        1            |                         |          |    1 |   1  |
| 0   | 1   | 1   | 0   | 0   |         1           |                         |     1     |     |    1 |
| 0   | 1   | 1   | 0   | 1   |          1          |                         |      1    |    1 |   1  |
| 0   | 1   | 1   | 1   | 0   |           1         |                         |          |     |     1|
| 0   | 1   | 1   | 1   | 1   |            1        |                         |          |   1  |   1  |
| 1   | 0   | 0   | 0   | 0   |                    |        1                 |    1      |     |   1  |
| 1   | 0   | 0   | 0   | 1   |                    |         1                |     1     |   1  |  1   |
| 1   | 0   | 0   | 1   | 0   |                    |          1               |          |     |    1 |
| 1   | 0   | 0   | 1   | 1   |                    |           1              |          |     1|   1  |
| 1   | 0   | 1   | 0   | 0   |                    |                         |  1        |     |    1 |
| 1   | 0   | 1   | 0   | 1   |                    |                         |   1       |    1 |   1  |
| 1   | 0   | 1   | 1   | 0   |                    |                         |          |     |     ==0==|
| 1   | 0   | 1   | 1   | 1   |                    |                         |          |     1|    1 |
| 1   | 1   | 0   | 0   | 0   |                    |                         |    1      |     |    1 |
| 1   | 1   | 0   | 0   | 1   |                    |                         |     1     |    1 |   1  |
| 1   | 1   | 0   | 1   | 0   |                    |                         |          |     |    ==0== |
| 1   | 1   | 0   | 1   | 1   |                    |                         |          |     1|    1 |
| 1   | 1   | 1   | 0   | 0   |                    |                         |      1    |     |    1 |
| 1   | 1   | 1   | 0   | 1   |                    |                         |       1   |    1 |   1  |
| 1   | 1   | 1   | 1   | 0   |                    |                         |          |     |     ==0==|
| 1   | 1   | 1   | 1   | 1   |                    |                         |          |     1|    1 |

# 5.

- A'B'C
- AB'C
- ABC

$(\neg A \cdot \neg B \cdot C) + (A \cdot \neg B  \cdot C) + (A \cdot B \cdot C)$

$(\neg A \cdot \neg B \cdot C) + (A \cdot \neg B  \cdot C) + AC$

$C\neg B + AC$


![[Diagram 32.svg]]

# 6.

a)


![[Diagram 33.svg]]

$B \neg C$
$AB$
$AC\neg D$
$A\neg B C$

b)

![[Diagram 34.svg]]

$\neg D B$
$AC$

$= \neg D B + AC$

c)

![[Diagram 35.svg]]

$CA$
$A \neg C$

$= CA + \neg C A$

# 7.