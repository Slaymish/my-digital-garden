---
{"dg-publish":true,"permalink":"/eeen-test-2-practice-questions/"}
---

Related: 
Contents: [[EEEN202/EEEN202 MOC\|EEEN202 MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-06-2023
***

# Question 1

a) 

```
accumulator 
timer unit
stack pointer register
Arithmetic Logic Unit
```

b)

```
ORG	0H ; ORG sets the memory locaiton of the location counter
```

c)
 
```
the stack pointer is a SFR that you can PUSH and POP memory addresses to, so you can back to them in the future. For example RET pops the top memory location of the SP and continues executing instructions from there.
```

d)

```
When an enabled interrupt is detected, it sets the interrupt flag to 1. This switches the executed instrucitons to a specifed place, regardless of what was executing at the time.
```

e)

```
Both SJMP and LJMP jump to the specified place in memory. The difference is SJMP uses relative addressing, which offsets where to execute by the opperands value (8-bit). LJMP uses 16-bit long addressing which means it can jump anyone in the codebase. Effectivley LJMP was jump further, and uses a more absolute addressing mode.
```

f)

```
When ACALL is called, it first increments the Program Counter register by 2. Then it pushes the memory location (16bit) specified to the Stack Pointer register using PUSH. It then increments the stack pointer twice.
```

g)

```
EQU allows you to set a symbolic name for a 16-bit value. This is similar to #define in C. The advantage of doing this is that you only have change it in one location if you need to change it
```

h)

```
ORG sets the memory location of the Program Counter Register. This is the register that always contains what the next instruction is.
```

i)

```
The main advantage is that it will likley be faster than using a higher level language if implemented correctly. 

A disadvantage is that due to the bareboneness of the microcontroller, it has limited memory. this is can make difficult to store data. Another program is that it is hardware dependant, meaning you have to code for the specific hardware you are using.
```

# Question 2 - [[Analogue to Digital Convertor\|Analogue to Digital Convertor]]

a)

```
sketch
```

b) [[Staircase ADC\|Staircase ADC]]

```
The main disadvantage of the staircase ADC is that it iterates through all possible voltages sequentually. This is slow, escpially if the voltage is on the upper end.

To improve it, you could use a successive approxmation convertor. This type of ADC makes big jumps between voltages, allowing the convertor to eliminate half the range at a time.
```

c)

```
input range/2^bits - 1
```

i) 
res = $\frac {10}{2^{14}-1}$
res = $\frac {10}{16383}$
res = $0.000610388817677$

ii)
6,094d
?? idk in binary

# Question 3 - [[Memory\|Memory]]

a)

```
SRAM: Static ram
SRAM perminatly holds the data stored on it while power is applied. Semiconductor memory

DRAM: Dynamic ram

FLASH: 
Shine uv light on transitor to write to it, acts as read-only memory
```

b)

I did this is [[EEEN Assignment 2\|EEEN Assignment 2]]
