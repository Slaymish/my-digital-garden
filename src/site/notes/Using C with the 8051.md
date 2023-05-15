---
{"dg-publish":true,"permalink":"/using-c-with-the-8051/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

- Assembly language codes usually require less memory and execute faster
- There is less number of restrictions compared to C

Good idea is to use a combination of both. Use a high lvl language for the bulk of the code and use assembly language coded interrupt routines or optimised functions for the time and memory demanding section

<p align="center">
Some C compilers allow you to add assembly code inline
</p>

![400][SCR-20230515-tkq.png]

As well as the basic primitive C data types, there datatypes specific to the microcontroller

# 8051 Compiler Specific Data Types

```
bit  - 0 to 1
sbit - 0 to 1
sfr - 0 to 255
sfr16 - 0 to 65535
```

# Internal Data Memory

- internal data can be broken down into three datatypes
	- data
	- idata
	- bdata

## Data

- Always refers to the first 128 bytes of internal data memory. Variables stored here are accessed using **direct addressing**

## Idata

- Refers to all 256 bytes of internal data memory

## Bdata

- refer to the 16 bytes of bit-adressable memory in the internal data area (20h to 2Fh)

### Examples:

```
unsigned char data name;
int idata count;
int bdata status;
```

## Bit-valued and Bit-Addressable Data

- The sbit datatype are used to declared var that access a specific bit field of a SFR or of a previously declared bit-addressable var

### Example

```
sbit X7_Flag = X^7; // bit 7 of X (bit variable)
sbit Red_LED = PO^1; // bit 1 of Port P0 (bit-addressable SFR)
```

- sbit **must** be a global variable
- X7_Flag is a 1-bit variable that reference bit number 7 of the integer  var X
- Red_LED refers to the bit number 1 


***

# External Data Memory

- up to 64kB

Two data types used to access external data:
- xdata
- pdata

