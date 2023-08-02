---
dg-home: false
dg-publish: true
---
Related: [[EEEN Sequential Logic]]
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 20-03-2023
***

# Familiarise Yourself With:

- Asynchronous ripple counters
- Ripple counters of arbitrary modulus
- Examples of shift register - counters
- The circuit implementation of some IC counters

***

# Pre Lab:

- [x] Sketch construction of a J-K flip flop and show how the design of this device can eliminate the occurrence of the clash state
- [x] Consider the J-K flip-flop with J=K=1 first in the SET state (Q=1) and then in the CLEAR state (Q=0) and show clearly explain what transition will occur in each case on the correct clock pulse. Use your sketch above to aid your explanation
- [x] Use a timing diagram to sketch the relationship between the incoming clock pulse and Q with the J-K flip flop in the toggle state (J=K=1)
- [x] Sketch how you will connect three such JK FF together to construct a 3 bit binary counter (also called a ripple counter)
- [x] Explain why this is an asynchronous counter
- [x] Obtain a data-sheet for the 74HCT112 dual JK FF and sketch the device pin-out

***

a. 

![[Diagram 4.svg]]
- When both J and K are high, the output is toggled
- Thus eliminating the clash state that occurs in a S-C FF


***

b. 

- If both J and K are high in the SET **or** CLEAR state, Q will toggle. This will happen on either a NGT or PGT.

***

c. 

- Use a timing diagram to sketch the relationship between the incoming clock pulse and Q with the J-K flip flop in the toggle state (J=K=1)


![[Diagram 5.svg]]

***

d. 

- Sketch how you will connect three such JK FF together to construct a 3 bit binary counter (also called a ripple counter)


![[Diagram 6.svg]]


***

e. 

- Explain why this is an asynchronous counter

Its an asynchronous counter because every FF except for the first is not tied to a CLK. It instead takes $\neg Q$ of the previous FF as the CLK. This makes it dependent of the JK input rather than the CLk.

***

f. 

[Data sheet](https://assets.nexperia.com/documents/data-sheet/74HC_HCT112.pdf)

![300][SCR-20230320-rus.png]
***

# Lab Procedure

```
// hthehheh
// this is the 
```

![[Pasted image 20230321104841.png]]

(i) To modify a Mod 16 counter to a Mod 12 counter, you need to add an AND gate that connects to the output of Q2 and Q3 (the 4-bit binary outputs: Q0, Q1, Q2, and Q3). The output of the AND gate will connect back to the reset input (RST) of the flip-flops.

When the counter reaches 1100 (binary for 12), the AND gate will activate the reset, forcing the counter back to 0000.

Table for first 14 input pulses:
Pulse     Q3 Q2 Q1 Q0
  0       0  0  0  0
  1       0  0  0  1
  2       0  0  1  0
  3       0  0  1  1 
  4       0  1  0  0
  5       0  1  0  1
  6       0  1  1  0
  7       0  1  1  1
  8       1  0  0  0
  9       1  0  0  1
 10       1  0  1  0
 11       1  0  1  1
(RST)     0  0  0  0
 12       0  0  0  1
 13       0  0  1  0

(ii) To modify a Mod 16 counter to a Mod 10 counter, you need to add a NAND gate which connects to the output of Q0 and Q3. The output of the NAND gate will connect back to the reset input (RST) of the flip-flops.

When the counter reaches 1010 (binary for 10), the NAND gate will activate the reset, forcing the counter back to 0000.