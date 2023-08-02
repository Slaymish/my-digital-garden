---
dg-home: false
dg-publish: true
---

# EEEN Lab 1 - Report Answers

Hamish Burke || 08-03-2023
***
Lab Partner: *Seb Collis*

## 8.1 One-bit Half Adder

1. Truth table

| A   | B   | SUM | CARRY |
| :-: | :-: |:---:|:-----:|
| 0   | 0   |  0  |   0   |
| 0   | 1   |  1  |   0   |
| 1   | 0   |  1  |   0   |
| 1   | 1   |  0  |   1   |

### Implementation

1. Using discrete logic gates
![[Diagram 1.svg]]

2. Using the 74HCT153 MUX

| A   | B   | I0a | I1a | I0b | I1b | S0  | SUM | CARRY    |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 1   | 0   | 0   | 0   | 0   | 0   |
| 0   | 1   | 0   | 1   | 0   | 0   | 1   | 1   | 0   |
| 1   | 0   | 1   | 0   | 0   | 1   | 0   | 1   | 0   |
| 1   | 1   | 1   | 0   | 0   | 1   | 1   | 0   | 1   |

To implement a half bit adder with the 74HCT153 MUX, you can use two multiplexers (one for sum, and one for carry). Below is where i'd connect each wire to create it:

**74HCT153 MUX #1 (SUM):**
-   Connect A to S0
-   Connect B to S1
-   Connect I0a to GND
-   Connect I1a to VCC
-   Connect I0b to GND 
-   Connect I1b to GND
-   The SUM output will be at Za

**74HCT153 MUX #2 (CARRY):**
-   Connect A to S0
-   Connect B to S1
-   Connect I0a to GND 
-   Connect I1a to GND
-   Connect I0b to GND
-   Connect I1b to VCC 
-   The CARRY output will be at Za


***

## 8.2 MUX Operations

### (i). Basic Operation of a 4:1 MUX

The 4:1 MUX selects one of several input signals and forwards the selected input to a single output line. It has four inputs and one output line. It also has two control lines called select lines that are used to choose which input line is connected to the output line.

| S1  | S0  | D0  | D1  | D2  | D3  | Y   |
| --- | --- | --- | --- | --- | --- | --- |
| 0   | 0   | l0  | 0   | 0   | 0   | l0  |
| 0   | 1   | 0   | l1  | 0   | 0   | l1  |
| 1   | 0   | 0   | 0   | l2  | 0   | l2  |
| 1   | 1   | 0   | 0   | 0   | l3  | l3    |

To implement logic functions using a 4:1 MUX, we can use the fact that the MUX can select one of several input lines based on the values of the select lines. We can use this property to create a circuit that performs any desired logic function.

### (ii). What Would the Internal Structure of a 2:1 MUX Look Like? (sketch)

![[Diagram 2.svg]]

### (iii). Discuss Operation of the 74HCT153 MUX

The 74HCT153 is a dual 4-input multiplexer that can select one of four input signals to pass through to the output based on the control inputs. The MUX can operate in two modes, as determined by the state of the mode select input.

When SEL is high (at 1), the MUX operates in the 4:1 MUX mode, where the two control inputs A and B select which of the four inputs (I0-I3) is routed to the output. The truth table for this mode is as follows:

| SEL | A   | B   | l0  | l1  | l2  | l3  | Y   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | 0   | 0   | D0  | D1  | D2  | D3  | Y0  |
| 1   | 0   | 1   | D4  | D5  | D6  | D7  | Y1  |
| 1   | 1   | 0   | D8  | D9  | D10 | D11 | Y2  |
| 1   | 1   | 1   | D12 | D13 | D14 | D15 | Y3    |

In this mode, the two ENABLE inputs function as active-low enable signals. When either enable input is low, the corresponding set of inputs (I0-I3 or I4-I7) is disabled and the output stays in a floating condition.

***

## 8.3 Prime Number Detector

1. Truth table (including any simplifications)

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

### Implementation

1. Using discrete logic gate
![[Diagram.svg]]


2. Using the 74LS153 MUX
**You will need two MUXs:**
- Connect $A$ to the select inputs ($S_1$ and $S_0$) of both MUX chips.
- Connect $\neg A$ to the two inputs of the first MUX (inputs $I_0$ and $I_1$).
- Connect $B$ to input $I_0$ of the second MUX, and connect $C$ to input $I_1$ of the second MUX.
- Connect the output of the first MUX to the select input ($S_1$) of the second MUX.
- Connect the output of the second MUX to the final output of the circuit.

	The final output will be $\neg AB + AC$.
	

3.  Which would result in the min number of ICs used?
	Using two of the 74LS153 MUX would be less than the four ICs needed using discrete logic gates

