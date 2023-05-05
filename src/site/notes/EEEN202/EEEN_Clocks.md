---
{"dg-publish":true,"permalink":"/eeen-202/eeen-clocks/"}
---

Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 13-03-2023
***

# Terminology

- Transitions are called *edges*
- Edges are whats important, not the HI/LO portions

## Positive Going Transition (PGT)

*When clock pulse goes from 0 to 1*

## Negative Going Transition (NGT)

*When clock pulse goes from 1 to 0*


![SCR-20230313-enb.png](/img/user/SCR-20230313-enb.png)


- Clock inputs labeled CLK,CK, or CP
- Activated with a PGT is there's a small triangle at CLK input
- Activated with a NGT is there's a bubble under that


![400][SCR-20230313-erz.png]

> [!Inputs]
> Control inputs have an effect on the output
> ONLY at the active clock transition (NGT or PGT)

***

## Clock Flip-flop
{ #b9278f}


*See [[EEEN202/EEEN Sequential Logic#^7a35e0\|more info here]]*
[[EEEN202/EEEN Sequential Logic#^d16fd0\|Applications]]

![SCR-20230313-ex4.png](/img/user/SCR-20230313-ex4.png)

### Internal Circuit of the Edge Triggered S-C FF

![400][SCR-20230313-f1q.png]
**Consists of:**
- A basic NAND gate latch (3 and 4)
- Pulse steering circuit (1 and 2)
- Edge detector circuit
	- Send CLK though invertor
	- Delay of invertor makes edge transition into a pulse

***

## Clocked J-K Flip-flop
{ #23e76d}


- Overcomes the disllallowed state of S-C FF
	- 1 & 1 for inputs
- J = set
- K = clear
- When both high, output is toggled to opposite state it is now
- Can be positive *or* negative going clock transition

| J   | K   | CLK | Q   |
| --- | --- | --- | --- |
| 0   | 0   | PGT |  $Q_0$ (no change)   |
| 1   | 0   | PGT |  1   |
| 0   | 1   | PGT |  0   |
| 1   | 1   | PGT |  $\neg Q_0$ (toggles)   |

**J-K Flip flop**
*ON NGT*

| J   | K   | CLK | Q                    |
| --- | --- | --- | -------------------- |
| 0   | 0   | NGT | $Q_0$ (no change)    |
| 1   | 0   | NGT | 1                    |
| 0   | 1   | NGT | 0                    |
| 1   | 1   | NGT | $\neg Q_0$ (toggles) |
|     |     |     |                      |

***

## Clock D Flip-flop

- One data input
- output changes to the values of the input at either PGT or NGT
- Can be implemented with a [[EEEN202/EEEN_Clocks#^23e76d\|J-K FF]]
	- By tying the J input to the K input through an inverter
- Useful for parallel data transfer

### Triggering on PGT

- Q (output) always same as D (input)


***

# Asynchronous Inputs

- Inputs that depend on the clock are synchronous
- Most clocked FF's have additional async inputs that do not depend on the clock
- These inputs are user to preset (Q=1) or clear (Q=0) the FF
	- active regardless of the state of the other inputs
- Also called **override inputs**
- If the asynchronous inputs are not used they will be tied to their inactive state



