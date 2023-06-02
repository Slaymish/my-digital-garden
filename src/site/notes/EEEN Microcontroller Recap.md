---
{"dg-publish":true,"permalink":"/eeen-microcontroller-recap/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-06-2023
***

# Main Components of a CPU (microcontroller)

- Program counter (**PC**) 
	- contains the address of the next instruction to be executed
- Instruction register (**IR**)
	- Contains binary code of instruction
	- OP code goes into instruction register
- Arithmetic and Logical unit (**ALU**)
	- Performs arithmetic and logic operations
- Stack Pointer (**SP**)
	- used to save data temporarily
	- acts as java stack (kinda)
- Registers
	- Temporary fast storage of information
- Instruction decoder timing and control unit
	- Interprets instructions and takes necessary action to execute it

## Components of a Microcomputer

Built up from a microprocessor. Add some memory and several I/O devices

- Address bus
- Data bus
- Control bus

![200][SCR-20230601-s8y.png]

> [!INFO]
> The Accumulator is really efficient, as its connected directly to the ALU

# 8051 Data Memory (RAM)

- Divided into three sections
	- Lower 128
		- Direct and Indirect Addressing
	- Upper 128
		- Indirect addressing only
	- [[Special function registers\|Special function registers]]
		- Direct Addressing only

- 384 bytes of memory total
- Upper 128 and SFR's share the same addresses from  **80H-FFH**

# Assembler Directives

- **Not** assembly language instruction as they don't generate any machine code
- Special codes placed in assembly program to instruct the assembler to perform a task or function
- Can be used to define symbol values, reserve & initialise storage space for vars

Typically specific to a particular assembler, we used **Keil A51 Assembler**

- Segment control
- Address control
- Symbol definition
- Memory initialisation/reservation

# Timer Mode1 (only This mode)

- 16-bit timer
- Counts up from value THx, TLx  and when it reaches max count value it sets the flag TFx and generates and interrupt 
- can 'poll' the TFx flag

# Execution Flow

- When an interrupt occurs, this is what happens

![250][SCR-20230601-sqy.png]


- Push PC on stack
- Push registers on stack
- Execute ISR code
- Pop registers
- Pop PC from stack

## Comparisons between Languages

- Assembly faster
	- Machine specific 
	- Harder
- Higher lvl language slower
	- But more portable/flexibility

