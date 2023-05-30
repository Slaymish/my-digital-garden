---
{"dg-publish":true,"permalink":"/types-of-memory/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 25-05-2023
***

# Types of Memory

## Volatile Memory

- requires electricity to retain information
- Typical semiconductor memory

***

## Non-Volatile Memory

- Retains memory when no electrical power is supplied
- Eg magnetic or optical memory

***

## Random Access Memory

- Memory where the physical location of the [[Memory#Memory Word\|memory word]] has no effect on how long it takes to access
- Same for all words in system

***

## Sequential Access Memory ([[SAM\|SAM]])

- The [[Memory#Access Time ($t_{ACC}$)\|access time]] isn't constant
- Depends on address location
- Used when memory words must be accessed in the same order every time
	- Eg DVD, video memory, even DRAM

***

## Read Write Memory ([[RWM\|RWM]])

- Memory that can be written to or read from with equal ease

***

## Read only Memory ([[ROM\|ROM]])

- For application with many read cycles, typically only one write cycle
- Alls ROM is **non volatile**
- Uses **address bus** (address inputs) to program it

**Applications**
- Embedded microcontroller program memory
- Data transfer/portability
- Data tables
- Function generator
- Auxiliary storage

### Mask Programmed ROM ([[MROM\|MROM]])

- photolithographic 'mask' establishes electrical interconnection
- Done during IC manufacturing process
- Not user programmable
- Really expensive to make a mask

### Electrically Erasable PROM ([[EEPROM\|EEPROM]])

- Uses a *special transistor* where a permanent charge is optionally stored that alter the behaviour of the transistor
- Voltage is use to **charge** or **discharge** memory element
- Individual bytes (words) can be erased, but often at a 'sector' at a time

#### Flash Memory (Type of EEPROM)

- Allow rapid in-circuit reprogramming of individual blocks
- Combines best features of EEPROM
- **All** flash memory is electrical variants of EEPROM
- Can shine light on transistor, UV light puts in into a blank state that we can write to

### Optical ROM

- Light is used to store binary data
- can store a large quantities of data
- CD,DVD's etc
- Can easily get scratched/ruined


***

## Static Memory Devices ([[SRAM\|SRAM]])

- **Semiconductor memory** in which stored data will remain permanently as long as power is applied **without need for refreshing** (re-writing the data)
- CMOS MCM6264C

![280][SCR-20230529-lpc.png]

***

## Dynamic Memory Devices ([[DRAM\|DRAM]])

- Semiconductor memory where the stored data **needs** to be constantly refreshed
- High capacity
- Low power requirement
- Moderate speed

- **Small capacitors** used to store data

### Structure and Operation

- Array of cells with unique row and col positions
- Analysis of read/write operations using:

![300][SCR-20230529-lr7.png]

### DRAM Refreshing

- When a read operation performed, all cells in **row** will be refreshed
- Refresh control logic is used to make sure each cell is refreshed within time limit

# Typical Setup

## Main Memory

- DRAM
- Typically stores the computers working memory
- Stores instructions and data that the CPU is currently working on

## Auxiliary Memory (mass storage)

- Stores large amount of data **external** to main memory
- Slower than main memory and always non-volatile
- SSD/Flashdrive

## Cache Memory

- SRAM
- High speed block of memory
- Operates between main memory and the CPU to optimise speed of the computer


