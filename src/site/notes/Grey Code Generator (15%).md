---
{"dg-publish":true,"permalink":"/grey-code-generator-15/"}
---


# Grey Code Generator (15%)

Related: 
Contents: [[EEEN202/EEEN202 MOC\|EEEN202 MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-04-2023
***

- Synchronous design
- 3 bit counter

| B2 | B1 | B0 | G2 | G1 | G0 |
|----|----|----|----|----|----|
| 0  | 0  | 0  | 0  | 0  | 0  |
| 0  | 0  | 1  | 0  | 0  | 1  |
| 0  | 1  | 0  | 0  | 1  | 1  |
| 0  | 1  | 1  | 0  | 1  | 0  |
| 1  | 0  | 0  | 1  | 1  | 0  |
| 1  | 0  | 1  | 1  | 1  | 1  |
| 1  | 1  | 0  | 1  | 0  | 1  |
| 1  | 1  | 1  | 1  | 0  | 0  |

1. Write down 3-bit grey code
	1. 8 codes
2. State transition diagram
	1. 8 states
3. J-K, D Excitation tables

![250][SCR-20230403-e7c.png]


***

## Excitation Tables

D:

| $Q_N$ | $Q_{N+1}$ | D   |
| ----- | --------- | --- |
| 0     | 0         | 0    |
| 0     | 1         |   1  |
| 1     | 0         |   0  |
| 1     | 1         | 1    |

JK:

| $Q_N$ | $Q_{N+1}$ | J   | K   |
| ----- | --------- | --- | --- |
| 0     | 0         | 0   | X   |
| 0     | 1         |   1  |  X   |
| 1     | 0         |   X  |  1   |
| 1     | 1         | X    |   0  |

| Present State |       |       |       | Next State |       |       | Required D I/P's |       |       |
| ------------- | ----- | ----- | ----- | ---------- | ----- | ----- | ---------------- | ----- | ----- |
| S             | $Q_2$ | $Q_1$ | $Q_0$ | $Q_2$      | $Q_1$ | $Q_0$ | $D_2$            | $D_1$ | $D_0$ |
| 0             | 0     | 0     | 0     | 1          | 0     | 0     | 1                | 0     | 0     |
| 0             | 0     | 0     | 1     | 0          | 0     | 0     | 0                | 0     |      |
| 0             | 0     | 1     | 0     | 0          |       |       |                  |       |       |
| 0             | 0     | 1     | 1     |            |       |       |                  |       |       |
| 0             | 1     | 0     | 0     |            |       |       |                  |       |       |
| 0             | 1     | 0     | 1     |            |       |       |                  |       |       |
| 0             | 1     | 1     | 0     |            |       |       |                  |       |       |
| 0             | 1     | 1     | 1     |            |       |       |                  |       |       |
| 1             | 0     | 0     | 0     |            |       |       |                  |       |       |
| 1             | 0     | 0     | 1     |            |       |       |                  |       |       |
| 1             | 0     | 1     | 0     |            |       |       |                  |       |       |
| 1             | 0     | 1     | 1     |            |       |       |                  |       |       |
| 1             | 1     | 0     | 0     |            |       |       |                  |       |       |
| 1             | 1     | 0     | 1     |            |       |       |                  |       |       |
| 1             | 1     | 1     | 0     |            |       |       |                  |       |       |
| 1             | 1     | 1     | 1     |            |       |       |                  |       |       |

***

# Logic

Options:
- Gates
- Muxes

With JK FF's:
- 3 JK FF (3bit)
- CLK goes into all three


![SCR-20230403-ekl.jpeg](/img/user/SCR-20230403-ekl.jpeg)

- Needs direction

![400][SCR-20230403-epm.png]



$D_2$

```
Q2/Q1 | 0  | 1
------+----+----
   0  | 1  | 0
------+----+----
   1  | 0  | 1
```

|            | $Q_1$ | $\neg Q_1$ |
| ---------- | ----- | ---------- |
| $Q_2$      | 1     | 0          |
| $\neg Q_2$ | 0     | 1           |

$D_2 = \neg Q_2 \cdot Q_1 + Q_2 \cdot \neg Q_1$

```
Q2/Q0 | 0  | 1
------+----+----
   0  | 0  | 1
------+----+----
   1  | 1  | 0
```

```
Q1/Q0 | 0  | 1
------+----+----
   0  | 0  | 0
------+----+----
   1  | 1  | 1
```

- If muxes instead of logic gates
	- 16 I/P
	- One out

**use:**
- D FF's
- MUXES


***

| Present State (S, Q2, Q1, Q0) | Next State (Q2+, Q1+, Q0+) | Required D Input (D2, D1, D0) |
|-------------------------------|----------------------------|-------------------------------|
| 0, 0, 0, 0                     | 0, 0, 0, 1                 | 0, 0, 1                       |
| 0, 0, 0, 1                     | 0, 0, 1, 1                 | 0, 1, 1                       |
| 0, 0, 1, 1                     | 0, 0, 1, 0                 | 0, 1, 0                       |
| 0, 0, 1, 0                     | 0, 1, 1, 0                 | 1, 1, 0                       |
| 0, 1, 1, 0                     | 0, 1, 1, 1                 | 1, 1, 1                       |
| 0, 1, 1, 1                     | 0, 1, 0, 1                 | 1, 0, 1                       |
| 0, 1, 0, 1                     | 0, 1, 0, 0                 | 1, 0, 0                       |
| 0, 1, 0, 0                     | 0, 0, 0, 0                 | 0, 0, 0                       |
| 1, 0, 0, 0                     | 1, 1, 0, 0                 | 1, 0, 0                       |
| 1, 1, 0, 0                     | 1, 1, 0, 1                 | 1, 0, 1                       |
| 1, 1, 0, 1                     | 1, 1, 1, 1                 | 1, 1, 1                       |
| 1, 1, 1, 1                     | 1, 1, 1, 0                 | 1, 1, 0                       |
| 1, 1, 1, 0                     | 1, 0, 1, 0                 | 0, 1, 0                       |
| 1, 0, 1, 0                     | 1, 0, 1, 1                 | 0, 1, 1                       |
| 1, 0, 1, 1                     | 1, 0, 0, 1                 | 0, 0, 1                       |
| 1, 0, 0, 1                     | 1, 0, 0, 0                 | 0, 0, 0                       |

Formulas for above table:
D0 = $\neg S Q_0 + S \neg Q_0$
D1 = $\neg S Q_2 Q_1 + S \neg Q_1 Q_0$
D2 = $\neg S Q_1 + S \neg Q_2 \neg Q_1$


D is $\neg (A \lor C) + \neg A * B$

D = $\neg B * \neg C + BC$


$

****


D = $\neg B * \neg C + B*C$

D = $\neg B * \neg C + B*\neg B * C$ (complement law)

D = $\neg B * \neg C + \neg B * B * C$ (complement law)

D = $\neg B * (\neg C + C)$ (distributive law)

D = $\neg B$ (complement law)




***


Starting with the expression:

D = $\neg B * \neg C + B*C$

Using distributive law, we can factor out $B$ to obtain:

D = $B * (\neg C + C) + \neg B * \neg C$

Since $\neg C + C$ evaluates to 1, we can simplify the expression to:

D = $B + \neg B * \neg C$

Using De Morgan's law, we can further simplify this expression as:

D = $B + \neg (\neg B * \neg C)$

D = $B + B*C$

Therefore, the simplified expression for D is $B + B*C$ or simply $B$.