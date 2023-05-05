---
{"dg-publish":true,"permalink":"/eeen-202/eeen-sequential-logic/"}
---


Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 10-03-2023
***

# Sequential Logic

- Combination of the combinational logic elements as well as memory elements

![500][SCR-20230310-r1t.png]

## Latch

- Asynchronous
	- No timing signal in system
- Output triggered by input


***

### The NAND Gate Latch
{ #ea60f4}


![400][SCR-20230310-r63.png]
- Output depends on startup

### Setting the NAND Latch

![400][SCR-20230310-vfc.png]

![500][SCR-20230313-e53.png]

| Set | Clear | Output    |
| --- | ----- | --------- |
| 1   | 1     | No change |
| 0   | 1     | Q = 1     |
| 1   | 0     | Q = 0     |
| 0   | 0     | Invalid*   |

*Produces $Q = \neg Q = 1$\*

### Problems

- Last line of truth table is bad
- not a synchronous device

### Alternative Presentations of a NAND Gate Latch:

![300][SCR-20230313-e86.png]

![300][SCR-20230313-e89.png]

## Application

- Eliminating mechanical switch bounce
	- Place switch before NAND latch
![200][SCR-20230313-ebf.png]


***

## NOR Gate Latch

![250][SCR-20230313-ehe.png]

- Similar to NAND latch but $Q$ and $\neg Q$ is reversed
- The output will change when the input is pulsed *high*
- To begin operation of latch at a known level, a pulse can be applied to the set or clear inputs when powered up

| SET | CLEAR | Out       |
| --- | ----- | --------- |
| 1   | 1     | Invalid*  |
| 0   | 1     | Q = 0     |
| 1   | 0     | Q = 1     |
| 0   | 0     | No change |

*Produces $Q = \neg Q = 0$


***

# Flip-flops
{ #1ab375}


- Synchronous
	- Triggered by a [[EEEN202/EEEN_Clocks\|clock]]

## Applications

- FF's are commonly used for storage and transfer of binary data

Data Transfer:
- Parallel transfers
	- Register contents are transferred all at the same time with a single clock cycle
	- transferring the bits simultaneously is parallel
- Serial transfers
	- Register contents are transferred one bit at a time, with a *clock pulse for each bit*
	- Slower but simpler than parallel transfers
	- Data IN is one input

### Shift Register

- Three bit 'register' contains three FF's
- Shift register contains two registers, and puts the data from one to the other

#### Shift Register Counters

- The output of the last FF in the register is then connected back to the fist FF in some way.

Related: [[EEEN202/EEEN Schmitt-Trigger Devices\|Schmitt-Trigger Devices]]









