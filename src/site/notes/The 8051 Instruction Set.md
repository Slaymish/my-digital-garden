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

### Boot Program Me







***

## Architecture and Memory Organisation

## Addressing Modes

## Instruction Types