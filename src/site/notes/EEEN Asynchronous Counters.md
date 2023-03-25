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





***



# Synchronous (Parallel) Counter