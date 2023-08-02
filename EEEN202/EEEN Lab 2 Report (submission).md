# Lab 2 Report

Hamish Burke || 22-03-2023
***

# Section 3

## 3.1 The Basic SC Latch

NOR gate latch truth table:

| SET | CLEAR | OUTPUT    |
| --- | ----- | --------- |
| 0   | 0     | No change |
| 1   | 0     | Q = 1     |
| 0   | 1     | Q = 0     |
| 1   | 1     | Invalid   |

b) 
When I turn S to 1, $Q=1$ and $\neg Q = 0$
$Q$ and $\neg Q$ stay the same when S is returned to 0

c)
When I set C to 1, $Q=0$ and $\neg Q = 1$
No change again when set back to 0

d)
When both S and C are set to 1, $Q$ and $\neg Q$ go to zero. This is an invalid state

e)
For (SC) $11 \implies 10 \implies 00$, $Q=1$ and $\neg Q =0$
For (SC) $11 \implies 01 \implies 00$, $Q=0$ and $\neg Q =1$

f)
It doesn't give a reproducible result

***

## 3.4 The Edge-Triggered D FF

1. Does the operation of the RESET and SET lines depend upon the clock status?

The operation of the RESET and SET lines does not depend upon the clock status. They are asynchronous inputs, meaning that they can reset or set the flip-flop regardless of the clock's state.

3. What is the timing relation between Q and the CLK signal using the oscilloscope?

- Toggles on the PGT of the CLK
- CLK is **twice** the frequency as toggle

***

## 3.5 The JK Edge-Triggered FF

Truth table:

| J   | K   | CLK | Q                 |
| --- | --- | --- | ----------------- |
| 0   | 0   | NGT | $Q_0$ (no change) |
| 1   | 0   | NGT | 1                 |
| 0   | 1   | NGT | 0                 |
| 1   | 1   | NGT | $\neg Q_0$ (toggles)                  |

- It toggles on the negative edge transition of the CLK
- The CLK has twice the frequency as the toggle

Waveform Sketch:
![[Diagram 5.svg]]


***

# Section 4

## 4.1 Design of a Latching Circuit

Working:

| TEMP (S) | RESET (C) | ALARM (Q) |     |
| -------- | --------- | --------- | --- |
| 0        | 0         | -         |     |
| 0        | 1         | 1         |   Reset (deactivate alarm)  |
| 1        | 0         | 0         |   Set (activate alarm)  |
| 1        | 1         | -         |     |

| SET (TEMP) | NOT SET    | RESET | Q (ALARM) | X               |
| ---------- | --- | ----- | --------- | --------------- |
| 0          |  1   | 0     | 1         | $\neg S \neg R$ |
| 0          | 1    | 1     | 0         | $\neg S R$      |
| 1          |  0   | 0     | 0         | $S \neg R$      |
| 1          | 0   | 1     |           | $SR$            |

![[Diagram 8.svg]]


***

## 4.2 Draw the Logic Diagram for a D FF Using only NOR Gates

- Can be implemented with a j-k FF by tying the J input to K input through an inverter


![[Diagram 9.svg]]

***

## 4.3

| X   | Y   | Z   | S   | C   | Q   |
| --- | --- | --- | --- | --- | --- |
| 1   | 1   |  1   |1    | 1    |  no chng   |
| 0   | 1   |  1   |    1 | 1    |  no chng   |
| 1   | 0   |  1   |    1 |  1   |  no chng   |
| 0   | 0   |  1   |    1 |   1  |   no chng  |
| 1    | 1    | 0    |   1  |  1   |   no chng  |
|  0   |  1   |  0   |    1 |   1  |   no chng  |
| 1    |  0   |   0  |  1   |   0  |  Q=0   |
| 0   |   0  |   0  |    0 |     1|    Q=1 |

![[Diagram 10.svg]]


***

## 4.4

| PRE | CLR | Q                 |
| --- | --- | ----------------- |
| 1   | 1   | Clocked operation |
| 0   | 1   | Q = 1             |
| 1   | 0   | Q = 0             |
| 0   | 0   | Not used          |

JK=1 mean toggle on NGT

![[Diagram 11.svg]]