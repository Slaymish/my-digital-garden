---
{"dg-publish":true,"permalink":"/memory/"}
---

Related: 
Contents: [[EEEN202/EEEN202 MOC\|EEEN202 MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 25-05-2023
***

# Memory

High-speed main memory = RAM
Slower external auxiliary memory = SSD/HDD


![300][SCR-20230525-nla.png]

- There's different [[Types of Memory\|Types of Memory]]

## Memory Cell

- A device or circuit used to store a single memory bit

EG:
- A [[EEEN202/EEEN_Clocks#Clock Flip-flop\|Flip-Flop]]
- A capacitor (charged/uncharged)

## Memory Word

- Group of bits (memory cells) that represents data or an instruction of some type
- Word sizes are usually 8-64bits

## Capacity

- Measure of the number of bits that can be stored in a memory device
- Also called **density**

### Density Calculation

- A memory consists of 4096 words of 20bits each
- Thus total capacity $= 4096*20=81920\ bits$
- ^ We have $4K * 20\ bits$
- Number of words typically represented as a multiple of 1024 ($2^{10} = 1K$)

> [!ALSO]
> $1M = 1.048,576=2^{20}$
> $1G=1,073,741,824=2^{30}$

## Address

- A unique num (binary/hex code) that identifies the location of a word in memory

| Addresses | Words  |
| --------- | ------ |
| 000       | Word 0 |
| 001       | Word 1 |
| 010       | Word 2 |
| 011       | Word 3 |
|           |        |

## Operations

### Read

- Also called a **fetch operation**
- Binary word stored in a specific memory location is sensed and transferred to another device

![300][SCR-20230525-noh.png]

### Write

- Also called a **store operation**
- New word placed at a memory location
- Replacing the word previously stored there

![300][SCR-20230525-nkh.png]

## Access Time ($t_{ACC}$)

- Amount of time required to perform a **read operation**


![750][SCR-20230525-nqk.png]


