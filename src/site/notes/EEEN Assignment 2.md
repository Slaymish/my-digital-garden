---
{"dg-publish":true,"permalink":"/eeen-assignment-2/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 19-05-2023
***

# Assignment 2

## 1. Architecture

a.  The AT89C51AC3 is 'binary compatible' with which popular microcontroller?

b.  What high-level computer architecture makes use of shared data and program memory

```

```

c. What high-level computer architecture makes use of separate data and program memories

```
Harvard Architecture 
```

d. Which architecture does the 8051 employ

```
Harvard Architecture 
```

e. What does CISC stand for, and is the 8051 an example of a CISC system

```
CISC stands for 'Complex Instruction Set Computing', which the 8051 microcontroller is an example of, concidering it has a veriety of preprogrammed instructions, like arithmetic, boolean operations, and timers
```

f. In a standard 8051, how many clock cycles result in one machine cycle

```
12 clock cycles per machine cycle
```

g. Given a 40MHz crystal, find the time (in $μs$) required for one machine cycle

```
Given a 40MHz crystal, the time required for one machine cycle in a standard 8051 microcontroller, which consists of 12 clock cycles, is 0.3 microseconds (μs).
```

h. Given a 12 Mhz crystal, find the time (in $μs$) required for one machine cycle

```
1 microsecond (μs)
```

## 2. Architecture

a. In a CPU, what does ALU stand for

```
Arithmetic Logic Unit
```

b. In the 8051, what is an alternative name for Register A?

```
The Accumulator
```

c. In the 8051, how many bits is Register A?

```
The Accumulator is an 8-bit register
```

d. In the 8051, what register holds the address of the next instruction to be executed

```
The Stack Pointer (SP)
```

e. What is 0d16 in hex?

```
0x10
```

f. What is a larger numerical value: 0d128 or 0xFF?

```
128 vs FF == 128 vs 255

0xFF is the larger value
```

g. What is a smaller numerical value: 0b10000000 or 0xFF?

```
0b10000000 = 128
0xFF = 255

0b10000000 is the smaller value
```

h. Highlight the lower nibble of this 8051 byte

0b==1010==1010

i. On the 8051, what does the NOP instruction do?

```
NOP is the 'No Operation' instruction

Causes no operations to take place for one machine cycle. Used generally for timing purposes.
```

j. On the 8051, what does the INC instruction do?

```
INC increments the value of the chosen register by 1. I the value of the register is 0xFF, incrementing it will cause it to reset to 0. 
```

## 3. Memory

a. 

```
The 8051 reverses 8 bytes for each ISR.

If the code of an interrupt service routine is larger than the available 8 bytes, you would typically place the ISR code elsewhere in memory and use the 8 bytes to store a jump instruction to the location of the ISR code. 
```

*** b. 
What is internal data memory structure of the 8051 microcontroller?  
Explain each memory part. Which area is bit addressable? which area  
is only accessible using direct addressing?

Divided into three sections
	- Lower 128
	- Upper 128
	- Special function registers (SFR)

```
384 bytes of memory physically

Upper 128 and SFRs share the same addresses from location 80H to FFH
```

c.  

> [!FINISH]
> add timing diagram

## 4. Data Display

a.  **Che3ck working**

```
The advantage of storing a numerical value in BCD is that each number only changes one bit at a time. This means you can use the INC instruction to increment it by one.
```

b. What are the ASCII values of 0-9

| Number | Decimal | Hexadecimal |
|:------:|:-------:|:-----------:|
|   0    |   48    |     30      |
|   1    |   49    |     31      |
|   2    |   50    |     32      |
|   3    |   51    |     33      |
|   4    |   52    |     34      |
|   5    |   53    |     35      |
|   6    |   54    |     36      |
|   7    |   55    |     37      |
|   8    |   56    |     38      |
|   9    |   57    |     39      |

c. What does the DA instruction do? **

```
Decimal Adjust Accumulator

Adjusts the contents of the Accumulator to correspond to a BCD (Binary Coded Decimal) number
```

d. What instructions must be performed *before* the DA instruction

```
Before the DA instruction can be call, you should call the ADD or ADDC instructions. These add two BCD numbers together
```

e. Show how ASCII numerical data could be displayed, if R0 contains a number between 0-255 which is stored in binary format

- send is a subroutine 

```assembly
mov a, R0 ; copy R0 to accumulator
div ab ; divide accumulaotor by 10

add a, #30h 
acall send;   ; send high didit

mov a, b
add a, #30h
acall send   ; send low digit

send: 
	MOV P1, A ; Move the data from the accumulator to Port1 
	CLR P3.0 ; Make RS=0 for command register 
	CLR P3.1 ; Make RW=0 for write operation 
	SETB P3.2 ; Make E=1 to enable (assuming E is connected to P3.2) 
	ACALL DELAY; 
	CLR P3.2 ; Make E=0 to latch in the data 
	RET 
```

f. Show how ASCII numerical data could be displayed, if R1 contains a number between 0-99 which is stored in BCD format **

```assembly
MOV a, R1        ; Copy R1 to accumulator
SWAP a           ; Swap nibbles, now tens digit is in lower nibble
ANL a, #0Fh      ; Mask high nibble

ADD a, #30h      ; Convert to ASCII
MOV R2, a        ; Store the result in R2

MOV a, R1        ; Copy R1 to accumulator again
ANL a, #0Fh      ; Mask high nibble

ADD a, #30h      ; Convert to ASCII
MOV R3, a        ; Store the result in R3

MOV R1, R2       ; Move the tens digit to R1
ACALL send       ; Send tens digit to LCD

MOV R1, R3       ; Move the ones digit to R1
ACALL send       ; Send ones digit to LCD
```

## 5. Analog to Digital Conversion

a.

|             | Flash ADC                                                                            | Staircase ADC                                                                                              | Successive approx ADC |
| ----------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------- | --------------------- |
| Complexity  | High                                                                                 | Low                                                                                                        | Medium                |
| Cost        | High                                                                                 | Low                                                                                                        | Medium                |
| Speed       | Very High                                                                            | Low                                                                                                        | High                  |
| Description | Uses a resistor ladder and comparators to convert the analog signal in a single step | Uses a counter that makes a signal that ramps up until it matches the input signal, then outputs the count | Uses a binary search through all possible quantisation levels to converge on the input signal level                    |

b.

```
Output of 0 - 3.3V over a measuring range of 0-800°C
```

i) By how much would the output of a 12-bit ADC with a 0-5V input range change over the full input range of the thermocouple

```
0.00122 V per disvison
3.3V/0.00122 = 2705 steps up to 3.3V

temp resolution: 800/2705 = 0.296 degrees celcius
```

ii) What would the temperature resolution of this system be?

$Resolution = \frac{Full \ scale \ analog \ output}{2^2-1}=K$


iii) What would the temperature resolution be if a 16-bit ADC was used?

```

```

## 6. Writing Assembly Code

```assembly
addition between (contents of mem value given by contents register R0, and content of memory location 7Ah)

Subtract value in R4 from result

Rotate result 2bits to the right

Save the value of the current register bank
Stored in R3 register of register bank 2. Load the saved register bank
```

```assembly
MOV R0, #7Ah ; Load the memory location into R0
MOV A, @R0 ; Load the contents of the memory location into the accumulator
ADD A, R4 ; Add the contents of R4 to the accumulator
SUBB A, R4 ; Subtract the contents of R4 from the accumulator
RR A ; Rotate the accumulator right by 1 bit
RR A ; Rotate the accumulator right by 1 more bit
PUSH PSW ; Save the current register bank
MOV PSW, #20h ; Switch to register bank 2
MOV R3, A ; Store the result in R3 of register bank 2
POP PSW ; Restore the original register bank
```