---
dg-home: false
dg-publish: true
---
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 13-03-2023
***

# Pre-lab

[[EEEN Sequential Logic#^ea60f4]] - Link to notes
***
[[EEEN Lab 2 Report Task]]

## 2.1

*Show the construction of a basic NAND gate latch and use a truth table to show how the outputs depend on the inputs*

![[SCR-20230313-e53 1.png]]

| SET | CLEAR | OUT       |     | 
| --- | ----- | --------- | --- |
| 1   | 1     | No Change   |     |
| 0   | 1     | Q = 1     |  Latch is in SET   |
| 1   | 0     | Q = 0     |   Latch is in RESET  |
| 0   | 0     | Invalid |    Undesired state |

***

## 2.2

*Identify at least three different limitation of this basic S-C latch and show how each of these will be solved to produce a practical J-K flip-flop*

**Limitations:**
1. Unable to toggle its output state when both inputs are high. This can be solved in a J-K flip-flop by using the J and K inputs, which allow for toggling of the output state regardless of the input state.

2. Not a synchronous device (not tied to a clock). Solved in a J-K flip-flop by using a clock signal, which synchronizes the inputs and outputs

3. Sensitive to noise interference, which can cause unintended state changes. 

***

## 2.3

*The J-K flip flop has two inputs; show how this design can be modified to produce a D flip flop with a single data input*


**Truth table for a clocked J-K Flip Flop (triggers on PGT)**

| J   | K   | CLK | Q                    |
| --- | --- | --- | -------------------- |
| 0   | 0   | PGT | $Q_0$ (no change)    |
| 1   | 0   | PGT | 1                    |
| 0   | 1   | PGT | 0                    |
| 1   | 1   | PGT | $\neg Q_0$ (toggles) |

**Triggering on NGT**

| A   | B   | CLK | Q                    |
| --- | --- | --- | -------------------- |
| 0   | 0   | NGT | $Q_0$ (no change)    |
| 1   | 0   | NGT | 1                    |
| 0   | 1   | NGT | 0                    |
| 1   | 1   | NGT | $\neg Q_0$ (toggles) |

Can be implemented using a J-K flip flop by tying the J input to the K input through an inverter.
![[brave_39Owi1AydM.png]]

***

# In Lab

## Section 3

### 3.1 The Basic SC Latch

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

### 3.4 The Edge-Triggered D FF

1. Does the operation of the RESET and SET lines depend upon the clock status?

The operation of the RESET and SET lines does not depend upon the clock status. They are asynchronous inputs, meaning that they can reset or set the flip-flop regardless of the clock's state.

3. What is the timing relation between Q and the CLK signal using the oscilloscope?

- Toggles on the PGT of the CLK
- CLK is **twice** the frequency as toggle

***

### 3.5 The JK Edge-Triggered FF

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
