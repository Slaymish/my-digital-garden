---
{"dg-publish":true,"permalink":"/multiplexing-ic/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-04-2023
***

Is a [[EEEN Special Logic Function ICs\|EEEN Special Logic Function ICs]]

# Multiplexers (MUX)

- Selects on of multiple input signals and passes it to output
- SELECT input code determines which input is transmitted to output z


### Two-input multiplexer

| S   | Output   |   
| --- | --- | 
| 0   |  $Z=l_0$   |     
| 1   |  $Z=l_1$   |    


### Four-input multiplexer

| $S_1$ | $S_2$ | Output  |
| ----- | ----- | ------- |
| 0     | 0     | $Z=l_0$ |
| 0     | 1     | $Z=1_1$ |
| 1     | 0     | $Z=l_2$ |
| 1     | 1     | $Z=l_3$ |


# 74ALS151 MUX
*same as 74HC151*

| $\neg E$ | $S_2$ | $S_1$ | $S_0$ | $Z$   |
| -------- | ----- | ----- | ----- | ----- |
| H        | X     | X     | X     | L     |
| L        | L     | L     | L     | $l_0$ |
| L        | L     | L     | H     | $l_1$ |
| L        | L     | H     | L     | $l_2$ |
| L        | L     | H     | H     | $l_3$ |
| L        | H     | L     | L     | $l_4$ |
| L        | H     | L     | H     | $l_5$ |
| L        | H     | H     | L     | $l_6$ |
| L        | H     | H     | H     | $l_7$ |

