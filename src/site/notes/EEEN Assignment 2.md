---
{"dg-publish":true,"permalink":"/eeen-assignment-2/"}
---

Related: 
Contents: [[EEEN202/EEEN202 MOC\|EEEN202 MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 19-05-2023
***

# Assignment 2

## 1. Architecture

a.  The AT89C51AC3 is 'binary compatible' with which popular microcontroller?

```
The DS89C450 is binary compatible with it, meaning code written for one, can usually run on the other without modification
```

b.  What high-level computer architecture makes use of shared data and program memory

```
The Von Neumann architecture
```

c. What high-level computer architecture makes use of separate data and program memories

```
The Harvard Architecture 
```

d. Which architecture does the 8051 employ

```
The Harvard Architecture
```

e. What does CISC stand for, and is the 8051 an example of a CISC system

```
CISC stands for 'Complex Instruction Set Computing', which the 8051 microcontroller is an example of, concidering it has a veriety of preprogrammed instructions, like arithmetic, boolean operations, and timers.
```

f. In a standard 8051, how many clock cycles result in one machine cycle

```
12 clock cycles per machine cycle
```

g. Given a 40MHz crystal, find the time (in $μs$) required for one machine cycle

$T=1/40MHz$
$1\ Machine\ Cycle = 12 * 0.025$
$1\ Machine\ Cycle = 0.3 \mu s$

```
Given a 40MHz crystal, the time required for one machine cycle in a standard 8051 microcontroller, which consists of 12 clock cycles, is 0.3μs.
```

h. Given a 12 Mhz crystal, find the time (in $μs$) required for one machine cycle

```
1 microsecond (μs)
```

<br><br>

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
The Accumulator is an 8-bit register (1 byte)
```

d. In the 8051, what register holds the address of the next instruction to be executed

```
The Stack Pointer (SP)
```

e. What is 0d16 in hex?

```
0x10 or just 10
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
INC increments the value of the chosen register by 1. If the value of the register is 0xFF, incrementing it will cause it to reset to 0. 
```

<br><br>

<br><br>

## 3. Memory

a. 

```
The 8051 reverses 8 bytes for each ISR.

If the code of an interrupt service routine is larger than the available 8 bytes, you would place the ISR code elsewhere in memory and use the 8 bytes to store a jump instruction to the location of the ISR code. 
```

b.  What is the internal data memory structure of the 8051 microcontroller?  

```
The internal memory structure of the 8051 consists of 3 sections. The lower 128bits, the upper 128 bits, and the Special function registers (SFR). The SFR area has 21 addresses, out of which 11 are bit-addressable SFR locations. The memory addresses 00h-7Fh are bit-addressable. Also, Registers with byte addresses ending with 0h or 8h are also bit-addressable.
```

c.  

![file.jpeg](/img/user/file.jpeg)

<br><br>

<br><br>
<br><br><br><br>

## 4. Data Display

a. 

```
An advantage to using BCD is that its easier to convert BCD to decimal and vice versa compared to binary to decimal, because each digit is represented separately in BCD, reducing the complexity involved with converting it.

A disadvantage is that BCD is less space effiecent than regular binary as it has to retain the formatting of 4bits per decimal digit. Binary doesn't have to stick to this, so for something like '99', it takes 8bits in BCD, and 7bits in binary. This space ineffciency would increase with bigger numbers.
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
Stands for Decimal Adjust

Adjusts the contents of the Accumulator to correspond to a BCD (Binary Coded Decimal) number
```

d. What instructions must be performed *before* the DA instruction

```
Before the DA instruction can be call, addition must be performed on the BCD numbers. This could be done with the ADD or ADDC instructions. 
```

e. Show how ASCII numerical between 0-255 could be display, which is stored in binary format

- WRITE_TO_DISPLAY is a subroutine

```assembly
mov a, R0 ; copy R0 to accumulator
div ab ; divide accumulaotor by 10

add a, #30h 
acall WRITE_TO_DISPLAY;   ; send high didit

mov a, b
add a, #30h
acall WRITE_TO_DISPLAY   ; send low digit
```

f. Show how ASCII numerical data could be displayed, if R1 contains a number between 0-99 which is stored in BCD format

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
ACALL WRITE_TO_DISPLAY       ; Send tens digit to LCD

MOV R1, R3       ; Move the ones digit to R1
ACALL WRITE_TO_DISPLAY       ; Send ones digit to LCD
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
0.001221001221001 V per disvison

3.3 / 0.001221001221001 = 2,702.7
```

ii) What would the temperature resolution of this system be?

$3.3V/0.00122 = 2705$ steps up to 3.3V
Temperature Resolution =  $800/2705 = 0.296$ degrees celsius


iii) What would the temperature resolution be if a 16-bit ADC was used?

$Resolution=\frac{5}{2^{16}-1}$
$=\frac{5}{65535}$
$0.000076295109483$

$3.3V/0.000076295109483=43,253.1$
$Temperature Resolution = 800/43,253.1 = 0.01849578412$

$$0.0184958 ˚C$$

<br>

## 6. Writing Assembly Code

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
