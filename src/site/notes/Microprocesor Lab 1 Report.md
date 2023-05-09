---
{"dg-publish":true,"permalink":"/microprocesor-lab-1-report/"}
---

Hamish Burke || 09-05-2023
***

# Microprocesor Lab 1 Report

## Hex to Instruction Set:

Decoded HEX by going through instruction table.

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

***

## Decoded

Then put code into functions, and changed memory addresses to function name

```
ORG	0H

MOV	A,#38H		
ACALL	COMNWRT    	
ACALL	DELAY 

MOV	A,#0EH     	
ACALL	COMNWRT		
ACALL	DELAY

MOV	A,#01     	
ACALL	COMNWRT    	
ACALL	DELAY	

MOV	A,#06H     	
ACALL	COMNWRT    	
ACALL	DELAY

MOV	A,#'H'     	
ACALL	DATAWRT    	
ACALL	DELAY

MOV	A,#'E'     	
ACALL	DATAWRT    	
ACALL	DELAY

MOV	A,#'L'     	
ACALL	DATAWRT    	
ACALL	DELAY

MOV	A,#'L'     	
ACALL	DATAWRT    	
ACALL	DELAY	

MOV	A,#'O'     	
ACALL	DATAWRT

AGAIN:	
	SJMP	AGAIN      	
COMNWRT:                   	
		MOV	P1,A       	
		CLR	P2.0       	
		CLR	P2.1       	
		SETB	P2.2       	
		ACALL	DELAY		
		CLR	P2.2       	
		RET
DATAWRT:                   	
		MOV	P1,A       	
		SETB	P2.0       	
		CLR	P2.1       	
		SETB	P2.2       	
		ACALL	DELAY		
		CLR	P2.2       	
		RET


DELAY:	MOV	R3,#50 		
HERE2:	MOV	R4,#255		
HERE: 	DJNZ	R4,HERE 		
     	DJNZ	R3,HERE2
      	RET
	
		END
```