Hamish Burke || 30-03-2023

***

# Section 2

## 2.1 4-bit Ripple counter

![[Diagram 13.svg]]

![[Diagram 21.svg]]

| State | Q4 | Q3 | Q2 | Q1 |
|-------|----|----|----|----|
| 1     | 0  | 0  | 0  | 1  |
| 2     | 0  | 0  | 1  | 0  |
| 3     | 0  | 0  | 1  | 1  |
| 4     | 0  | 1  | 0  | 0  |
| 5     | 0  | 1  | 0  | 1  |
| 6     | 0  | 1  | 1  | 0  |
| 7     | 0  | 1  | 1  | 1  |
| 8     | 1  | 0  | 0  | 0  |
| 9     | 1  | 0  | 0  | 1  |
| 10    | 1  | 0  | 1  | 0  |
| 11    | 1  | 0  | 1  | 1  |
| 12    | 1  | 1  | 0  | 0  |
| 13    | 1  | 1  | 0  | 1  |
| 14    | 1  | 1  | 1  | 0  |
| 15    | 1  | 1  | 1  | 1  |
| 16    | 0  | 0  | 0  | 0  |
| 17    | 0  | 0  | 0  | 1  |
| 18    | 0  | 0  | 1  | 0  |

The mod number of a 4-bit counter is $2^4 = 16$, meaning the counter will cycle through 16 unique states (0000 to 1111) before repeating.

**Timing diagram:**

![[Diagram 14.svg]]

-   Q1: 500 Hz
-   Q2: 250 Hz
-   Q3: 125 Hz
-   Q4: 62.5 Hz

## 2.2 Modification of the Mod Number

To get the desired Mod 12 counter, I will put all the HI outputs from the first invalid state into a NAND gate, and connect that to the CLEAR inputs on all four FF's

| State | Q4  | Q3  | Q2  | Q1  |
| ----- | --- | --- | --- | --- |
| 1     | 0   | 0   | 0   | 1   |
| 2     | 0   | 0   | 1   | 0   |
| 3     | 0   | 0   | 1   | 1   |
| 4     | 0   | 1   | 0   | 0   |
| 5     | 0   | 1   | 0   | 1   |
| 6     | 0   | 1   | 1   | 0   |
| 7     | 0   | 1   | 1   | 1   |
| 8     | 1   | 0   | 0   | 0   |
| 9     | 1   | 0   | 0   | 1   |
| 10    | 1   | 0   | 1   | 0   |
| 11    | 1   | 0   | 1   | 1   |
| 12    | 0   | 0   | 0   | 0   |
| 13    | 0   | 0   | 0   | 1   |
| 14    | 0   | 0   | 1   | 0   |

***

# Section 3 - Counters

## 3.1 The Ring Counter

| Count | Q4  | Q3  | Q2  | Q1  |
| ----- | --- | --- | --- | --- |
| 1     | 1   | 0   | 0   | 0   |
| 2     | 0   | 1   | 0   | 0   |
| 3     | 0   | 0   | 1   | 0   |
| 4     | 0   | 0   | 0   | 1   |
| 5     | 1   | 0   | 0   | 0   |
| 6     | 0   | 1   | 0   | 0    |

The count sequence will continue to rotate through the initial binary value "1000" indefinitely.

## 3.2 Twisted Ring Counter

| Count | Q4 | Q3 | Q2 | Q1 |
|------|----|----|----|----|
| 1    | 1  | 1  | 1  | 1  |
| 2    | 0  | 1  | 1  | 1  |
| 3    | 0  | 0  | 1  | 1  |
| 4    | 0  | 0  | 0  | 1  |
| 5    | 1  | 0  | 0  | 0  |
| 6    | 1  | 1  | 0  | 0  |
| 7    | 1  | 1  | 1  | 0  |
| 8    | 1  | 1  | 1  | 1  |

It'll repeat from after  the 8th state


***

# Section 4

## 1.2 kHz Signal Generation

- $18 kHz / 1.2 kHz = 15$
- Trying to make a counter that divides by 15 (mod 15)
- On 15th state, reset counter

$15 = 2^n$
$n= 3.9$
Number of FF $= 4$

### I. Logic Diagram

![[Diagram 17.svg]]

### Ii. Circuit Diagram with 74HCT112 JK FF ICs

![[Diagram 19.svg]]

***

## Frequency Divider from 50 Hz to 1 Hz

  J  |  K  |  CLK  |  Q(t)  |  Q(t+1)
-----|-----|-------|--------|---------
  0  |  0  |   X   |   Q    |    Q
  0  |  1  |   ↑   |   Q    |    0
  1  |  0  |   ↑   |   0    |    Q
  1  |  1  |   ↑   |  ~Q    |    Q

MOD/CLK = 1

MOD = 50
$2^n=50$

$n = 5.5$
$n = 6$
Use 6 FF's

-  Use a 6-stage binary counter with JK Flip Flops. Connect the output of each flip flop to the clock input (CLK) of the next flip flop. Set the J and K inputs of each flip flop to 1, so they act as toggle flip flops.

-  Use a 3-input AND gate to detect when the binary counter reaches 50 ($110010$ in binary). Use output of AND to reset counter

### I. Logic Diagram

![[Diagram 15.svg]]
\* error with above diagram: Inputs into AND gate should be reverse. It should be Q6, Q5, and Q2

### Ii. Circuit Diagram with 74LS293 Counter ICs

- Will need two ICs
	- IC1 = divide-by-5
	- IC2 = divide-by-10


![[Diagram 16.svg]]


***

## Mod 10 Counter on 7 Segment Display

1.  Connect the Mod 10 counter's Q0-Q3 outputs to the HCT4511's D1 to D4 inputs respectively. This will allow the binary coded decimal output from the Mod 10 counter to be passed to the HCT4511 decoder.  
2.  Connect HCT4511's outputs (Qa to Qg) to the corresponding inputs of the seven-segment display. 

![[Diagram 22.svg]]
![[Diagram 20.svg]]






