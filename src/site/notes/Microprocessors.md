---
{"dg-publish":true,"permalink":"/microprocessors/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 07-05-2023
***

# History

In **1959**, the very first integrated circuit was created. This circuit contained a single transistor and its supporting components.

Moving forward to **1981**, IBM created its original PC using the *Intel 8088 processor*, which contained a total of 29,000 transistors. The PC utilised the MS-DOS operating system, designed by Microsoft.

***

# Microprocessors

## ATMEL AT89C51AC3 Microcontroller

Microcontroller core:
![300][SCR-20230507-rdf.png]


[[Special function registers\|Special function registers]] perform specific functions like:
- Timer
- IO inputs

## Keys Parts
{ #a6ee6c}


**ALU: Arithmetic Logic Unit**
- Performs all arithmetic (addition, subtraction, multiplication, division)
- and logical (AND, OR, NOT, EXCLUSIVE-OR and rotating) operations 8 bit data

**PC: Program Counter**
- 16 bit register
- It always contains the memory address of the next instruction to be executed
- As the CPU fetches the op-code (instruction byte) from program memory
- The PC is incremented automatically to point to the next instruction


**Timer/Control and Instruction Unit**
- Responsible for decoding and managing the execution of instructions
- Accurately measure time

**SFRs**
- [[Special function registers\|Special function registers]]
- They are all the other register in the core and they are addressable

### SFR Mapping

![600][SCR-20230507-ruw.png]

***

## Accumulator

- Most useful and versatile register because it is used in 
	1. All arithmetic operations
	2. Majority of logical operations
	3. All data transfer between the 8051 and any external memory

## DPTR: Data Pointer

- 16 bit register
- Used to point to a data byte in external data (RAM) or program (ROM) memory

## SP: Stack Pointer

- Special area of memory allocated for temporary storage
- Often used to store the status of the core when the processor is switched to a different task
- Always points to the top of the stack
- 8-bit register
- The data is stored on the stack using PUSH and CALL instructions
- Retrieved using POP and RET instructions

## PSW: [[Program Status Word\|Program Status Word]]

- 8-bit register
- Also referred to as flag register or processor status word


***

## Memory

- Harvard Architecture
- Separate on-chip program and data memory
- Results in faster execution, because can access both at the same time


We are using this chip in  [[EEEN Lab 1 Hex\|EEEN Lab 1 Hex]]
- Good example of changing the checksum on the Intel Hex Wikipedia page

## Checksum

A checksum is a simple error-detection method used to ensure data integrity. It is a value calculated from a data set and transmitted or stored along with the data. When the data is read or received later, the checksum is recalculated from the received data and compared to the original transmitted value. If the two values match, it indicates that the data has not been altered during transmission or storage.

In the context of microcontrollers and Intel Hex files, a checksum is used to ensure that the program code and data have been transferred correctly to the target device. The checksum for each record in an Intel Hex file is calculated as an 8-bit sum of all byte values in that record, excluding the starting colon and any newline characters. The calculated checksum is then stored as a 2-digit hexadecimal number at the end of each record.

If there are any errors in transmission or storage, such as bit flips or lost bytes, they will likely cause a mismatch between the original and recalculated checksums when verifying the Intel Hex file contents. In such cases, an error message will be generated, alerting users to potential issues with their program code or data.