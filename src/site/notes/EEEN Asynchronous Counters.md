---
{"dg-home":false,"dg-publish":true,"permalink":"/eeen-asynchronous-counters/","dgPassFrontmatter":true}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 25-03-2023
***

- Main applications of Flip Flops is as counters
- Combining FFs and logic gates to form various counters configs

> [!INFO]
> One FF = one bit


Counting states:
- Eg want a counter with 13 counting states
	- would count from 0-12
	- Need 4 bits

# Whats a counter?
- Will count (and display) the number of times a event occurs
- If the clock pulses (the event) are of a calibrated frequency
	- eg f=1hz, can turn our counter into a timer
- Normally output in binary (or BCD)


***


# Asynchronous Counters
- Every bit in the counter output code is the output from one sequential element ([[EEEN202/EEEN_Clocks#^b9278f\|FF]]). These bits do not all change at the same time (not synchronised)
- Each FF are thus driven by a *different* clock
![400][SCR-20230325-nfn.png]

One bit counter?
- A synchronous JK flipflop in the toggle state


### 4-bit async counter
- AKA Ripple counter
- Outputs A,B,C,D are the binary output
![380][SCR-20230325-nji.png]

- Cascading toggling
![400][SCR-20230325-nkw.png]

- In 1111 counting state
	- The NT of the 16th clock pulse is what resets it
	- A will toggle first, then others with follow
	- Thats the reason its not synchronous
	- 80 nanoseconds to reset

### MOD number
- Equal to the number of *states* that a counter goes through before recycling
- MOD num = $2^n$ 
	- n = number of flip-flops

### Frequency Division
- Output of last FF divides the input clock frequency by the MOD num
	- Eg 4 bit counter with 16hz clock
		- $2^4/16$ = 1hz (final FF frequency)


## Counters with MOD Num $<2^N$
- Counter can be designed to reset on a specific counter state
- If asked to make counter with MOD 50
	- Counter will go from 0-49
	- MOD num should be the first invalid counting state
	- Should reset on 49th counting state
![400][SCR-20230325-nx6.png]

### Changing the MOD Num
- Find smallest MOD required so $2^N$ is greater or equal to the requirements
	- Determines the num of FF's needed
- Connect a NAND gate to the async CLEAR inputs on all FF's
- Determine which FF's are HIGH at the first undesired state
	- Connect the outputs of the FF's to the NAND gate inputs


### BCD/Decade counter
- 10 distinct states
- Any MOD-10 counter is a decade counter
- A BCD counter is a decade counter that counts from 0000 to 1001

# 74LS293
![480][SCR-20230325-o56.png]
- Has two different clock pulses
- Can use as three bit counter (ignore first FF)
- For 4bit counter, $Q_0$ has to connect to $CP_1$

