---
{"dg-publish":true,"permalink":"/eeen-lab-microcontrollers/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-05-2023
***

# Modes

```
#data = 8-bit constant included
```

## Instruction Definitions

```
MOV A,#data - Move immediate data to the acumulator
ACALL addr11 - Absolute subroutine call



11: ACALL code_addr
43: ORL data_addr, #data - bit atom (operates on a0)



bits not printed: 46
bits printed: 43


need to convert go to (11) addr to binary then count it out

Report:
- assembly code
- data vars, as actual numbers



```

## Addressing Modes

| Addressing modes   | Instruction    |
| ------------------ | -------------- |
| Register           | MOV A,B        |
| Direct             | MOV 30H,A      |
| Indirect           | ADD A,@R0      |
| Immediate Constant | ADD A,#80H     |
| Relative           | SJMP AHEAD     |
| Absolute           | AJMP BACK      |
| Long               | LJMP FAR_AHEAD |
| Indexed            | MOVC A,@A+PC   |

## Register Addressing

- The register addressing instruction involves information transfer between registers
- eg
	- MOV R0,A
	- The instruction transfers the accumulator content into the R0 register. THe register bank (Bank 0,1,2, or 3) must be specified prior to this instruction

## Direct Addressing

- Allow you to specify the operand by giving its actual memory address
- eg
	- MOV A, P3
		- Transfer the contents of port 3 to the accumulator
	- MOV A, 020H
		- Transfer the contents of RAM location 20H to the accumulator

## Indirect Addressing

- Uses a pointer to hold the effective address of the operand
- Only registers R0,R1 and DPTR can be used as the pointer register
- R0 and R1 registers can hold an 8-bit address, whereas DPTR can hold a 16-bit address
- eg
	- MOV @R0,A
		- store the content of accumulator into the memory location pinted to by register R0. R0 could have an 8-bit address such as 60H
	- MOVX A, @DPTR
		- Transfer the contents from the memory location pointed to by DPTR into the accumulator. DPTR could have a 16-bit address, such as 1234H.

## Hex to Instruction Set:

```
74: MOV (A,#data)
38: ADDC A,R0
	11: ACALL code_addr
	36: ADDC A,@R0
11: ACALL code_addr
50: JNC code_addr
74: MOV (A,#data)
0E: INC R6
11: ACALL code_addr
36: ADDC A,@R0
11: ACALL code_addr
50: JNC code_addr
74: MOV (A,#data)
01: AJMP code_addr
	11: ACALL code_addr
	36: ADDC A,@R0


11: ACALL code_addr
50: JNC code_addr
74: MOV (A,#data)
48: H
	11: ACALL code_addr
	36: ADDC A,@R0
11: ACALL code_addr
50: JNC code_addr
74: MOV (A,#data)
			48: ORL A,R0 - H
11: ACALL code_addr
43: ORL data_addr, #data
11: ACALL code_addr
50: JNC code_addr
74: MOV (A,#data)
			45: ORL A,data_addr - E


11: ACALL code_addr
==43==: ORL data_addr, #data
11: ACALL code_addr
50: JNC code_addr
74: MOV (A,#data)
			4C: ORL (A,R4) - L
11: ACALL code_addr
50: JNC code_addr
74: MOV (A,#data)
			4C: ORL (A,R4) - L
11: ACALL code_addr
==43==: ORL data_addr, #data
11: ACALL code_addr
50: JNC code_addr


74: MOV (A,#data)
			4F - O
11: ACALL code_addr
==43==: ORL data_addr, #data
80: SJMP (code addr)
FE: MOV (R6,A)
F5: MOV (data addr, A)
90: MOV (DPTR,#data)
C2: CLR (bit addr)
A0: ORL (C,bit addr)
C2: CLR (bit addr)
A1: AJMP (code adrr)
D2: SETB (bitaddr)
A2: MOV (C,bit addr)
11: ACALL code_addr
50: JNC code_addr


C2: CLR (bit addr)
A2: MOV (C,bit addr)
22: RET
F5: MOV (data addr, A)
90: MOV (DPTR,#data)
D2: SETB (bit addr)
A0: ORL (C,bit addr)
C2: CLR ()
A1: AJMP (code adrr)
D2: SETB (bitaddr)
A2: MOV (C,bit addr)
11: ACALL code_addr
50: JNC code_addr


7B: MOV (R3,#data)
32: RETI
7C: MOV (R4,#data)
FF: MOV (R7,A)
DC: DJNZ (R4, code addr)
FE: MOV (R6,A)
DB: DJNZ (R3,code addr)
FA: MOV (R2,A)
22: RET

```

## V2

```
74: MOV (A,#data)
	38: ADDC A,R0
11: ACALL code_addr
	36: ADDC A,@R0

11: ACALL code_addr
	50: JNC code_addr
74: ACALL code_addr
	0E: INC R6
11: ACALL code_addr
	36: ADDC A,@R0
11: ACALL code_addr
	50: JNC code_addr
	
74: MOV (A,#data)
	01: AJMP code_addr
11: ACALL code_addr
	36: ADDC A,@R0

11: ACALL code_addr
	50: JNC code_addr

74: MOV (A,#data)
	48: ORL A,R0 ==== H
11: ACALL code_addr
	36: ADDC A,@R0

11: ACALL code_addr
	50: JNC code_addr
	
74: MOV (A,#data)
	48: ORL A,R0 ==== H
11: ACALL code_addr
	43: ORL data_addr, #data
	
11: ACALL code_addr
	50: JNC code_addr ===== E
74: ACALL code_addr
	45: ORL A,data_addr

11: ACALL code_addr
	43: ORL data_addr, #data
11: ACALL code_addr
	50: JNC code_addr
	
74: MOV (A,#data)
	4C - L
11: ACALL code_addr
	50: JNC code_addr
	
74: MOV (A,#data)
	4C - L
11: ACALL code_addr
	43: ORL data_addr, #data
11: ACALL code_addr
	50: JNC code_addr

```