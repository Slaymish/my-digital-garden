---
{"dg-publish":true,"permalink":"/the-8051-instruction-set/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 08-05-2023
***

# 8051 Instruction Set

- An instruction is made up of an op-code follow by either zero, one or two bytes of operands
- The op-code shows the type of operation to be performed

# Architecture and Memory Organisation

## 8051 Data Memory

- Divided into three sections
	- Lower 128
	- Upper 128
	- [[Special function registers\|Special function registers]] (SFR)

**384** bytes of memory physically

Upper 128 and SFRs share the same addresses from location 80H to FFH

### Special Function Registers

- Provide control and data exchange with the microcontrollers resources and peripherals
- Registers which have their byte addresses ending with 0H or 8H are *byte* - as well as *bit* addressable
- Some registers are not bit-addressable
	- including stack pointer (SP)
	- and data pointer register (DPTR)

### FLASH Memory

- Can be reprogrammed in-circuit
- Non-volatile data storage
- Allows field upgrades of 8051 firmware
- FLASH is **65536 bytes**

### Boot Program Memory

- Flash memory architecture with ENBOOT=1 (boot mode)



***

# Addressing Modes

- 8 modes of addressing available

## Register Addressing

- Involves Information transfer between registers

### Example

```
MOV R0, A
	; Instruction transfer the accumulator content into the R0 register
	; The register bank (0,1,2,3) must be specified prior to this instruction
```

## Direct Addressing

- Specify the operand by giving its memory address 
- Typically specified in **Hex**
- Or giving its abbreviated name (eg P3)

### Example

```
MOV A, P3
	; Transfer contents of port 3 to the accumulator

MOV A, 020H
	; ransfer the contents of RAM location 20H to the accumulator
```

## Indirect Addressing

- Uses a pointer to hold the *effective address* of the operand
- Only register R0,R1, and DPTR can be used
- R0/R1 can hold 8-bit address, DPTR can hold 16-bit

### Example

```
MOV @R0,A
	; Store the conent of
	; accumulator into the memory
	; location pointed to by
	; register R0 (8-bit address)

MOVX A, @DPTR
	; Transfer content from the pointed 
	; memory location (16-bit address)
```

## Immediate Constant Addressing

- Uses 8/16bit constant value as the source operand
- Specified in the instruction, rather than memory location/register
- Dest register should hold the same data size as operand

### Example

```
ADD A, #030H
	; Add 8-bit value of 30H
	; to accumulator
	; (8-bit register)
	
MOV DPTR, #0FE00H
	; Move 16-bit data constant
	;into 16-bit data pointer register
```

## Relative Addressing

- Jumping around the program instructions
- Dest address must be with -128 to +127 bytes from the current instruction address
	- Because 8-bit offset is used

### Example

```
DEC A
	; Decrement A

JNZ GoBack
	; if A is not zero, loop back
```

## Absolute Addressing

- ACALL AJMP instructions
	- Two byte instructions where 11-bit absolute address is the operand
- Upper 5 bits not modified
- Lower 11bits are loaded from instruction

### Example

```
ACALL PORT_INIT
	; PORT_INIT should be located with 2k bytes

PORT_INIT: MOV P0, #0FH
	; PORT_INIT subroutine
```

## Long Addressing

- LCALL and LJMP
- 16-bit dest location
- Allows use of the full 64k code space
- Always branch to the same location no matter where

### Example

```
LCALL TIMER_INIT
	; TIMER_INIT address (16-bit long)

TIMER_INIT: ORL TMOD, #01H
	; TIMER_INIT subroutine
```

## Indexed Addressing

- DP register holds base address and the accumulator holds an 8-bit displacement or index value
- Sum of these two registers forms the effective address for a JMP or MOVC instruction

### Example

```
MOV A,#08H ; Offset from table start
MOV DPTR,#01F00H ; Table start addrs
MOVC A,@A+DPTR ; Gets target value from table start address + offset and it in A
```

- After execution, program will branch to address 1F08H (1F00H+08H) and transfer into the accumulator the data byte retrieved from the look-up table

***

# Instruction Types

## Arithmetic Operations

- CPU has no knowledge of the data format
- Appropriate status bits in the PSW are set when conditions are met

- [@Ri] implies contents of memory location pointed to by R0 or R1
- Rn refer to register R0-R7 of the currently selected register bank

## Logical Operations

- AND,OR,XOR,NOT
- On a bit-by-bit basis

### Examples

```
ANL A, #02H ; Mask bit 1
ORL TCON, A; TCON = TCON-OR-A
```

## Data Transfer Instructions

- Transfer data between an internal RAM location and an SFR location with going through the accumulator

## Boolean Variable Instructions

- Includes set, clear, and , or and complement
- Also bit-level moves or conditional jump instructions
- All bit accesses use direct addressing

### Examples

```
SETB TR0 ; Start Timer0
POLL: JNB TR0, POLL ; Wait till timer overflows
```

## Program Branching Instructions

- Used to control flow of program execution
- CJNE acts as if statement