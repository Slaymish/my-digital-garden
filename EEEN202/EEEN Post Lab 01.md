Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 13-03-2023
***

# Prime Number Detector

*Design a circuit that looks at a three-bit binary code (CBA) and out a HI signal if the decimal equivalent of the code represents a prime number*

1. 
| A   | B   | C   | Decimal |  OUT   | 
| --- | --- | --- | ------- | --- |
| 0   | 0   | 0   | 0       |   0  |
| 0   | 0   | 1   | 1       |   0  |
| 0   | 1   | 0   | 2       |   1  |
| 0   | 1   | 1   | 3       |  1   |
| 1   | 0   | 0   | 4       |   0  |
| 1   | 0   | 1   | 5       |   1  |
| 1   | 1   | 0   | 6       |   0  |
| 1   | 1   | 1   | 7       |   1  |


$\neg A B \neg C + \neg A BC + A \neg B C + ABC$
$\neg A B(\neg C + C)+AC(\neg B + B)$
$\neg A B + AC$


K-Map:

| |  $\neg C$   |  $C$   |
| --- | --- | --- |
| $\neg A \neg B$   |     |     | 
| $\neg A B$  |   T  |   T  |
| AB  |     |   T  |
| $A \neg B$   |     |    T |

![[Diagram.svg]]
