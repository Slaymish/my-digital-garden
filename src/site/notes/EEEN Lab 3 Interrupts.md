---
{"dg-publish":true,"permalink":"/eeen-lab-3-interrupts/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-05-2023
***



```assembly
		ORG	0H
		MOV	R0,#20
		MOV	R1,#0			//Set time value = 0, seconds, register 1
		MOV	R2,#0			//minutes, register 2
		MOV	R3,#0			//hours, register 3
		ACALL SETDIS		//initialise the display
		MOV TMOD,#0x01
REPEAT:	MOV	TH0,#0x3C
		MOV	TL0,#0xB0
		SETB TR0
WAIT:	JNB TF0,WAIT
		CLR TR0
		CLR TF0
     	DJNZ R0,REPEAT
		MOV	TH0,#0x3C
		MOV	TL0,#0xB0
		SETB TR0
		MOV	R0,#19
		CPL P2.3			//output every second
		ACALL INCT			//Increment time
		ACALL DIST			//Display time
		AJMP WAIT
		
SETDIS: MOV	A,#38H			//Display initialisation routine
		ACALL	COMNWRT    	
		ACALL	DELAY1      	
		MOV	A,#0EH     	
		ACALL	COMNWRT		
		ACALL	DELAY1		
		MOV	A,#01     	
		ACALL	COMNWRT    	
		ACALL	DELAY2		
		MOV	A,#06H     	
		ACALL	COMNWRT    	
		ACALL	DELAY1		
		RET
		
INCT:	MOV A,R1			//Update time count routine (seconds)
		ADD A, #01h
		DA A
		MOV R1, A
		CJNE R1, #60, INCE     //if time is not 60, return
		MOV	R1,#0
		
		MOV A,R2			//Update time count routine (minutes)
		ADD A, #01h
		DA A
		MOV R2, A
		CJNE R2, #60, INCE     //if time is not 60, return
		MOV	R2,#0
		
		MOV A,R3			//Update time count routine (hours)
		ADD A, #01h
		DA A
		MOV R3, A
		CJNE R3, #24, INCE     //if time is not 24, return
		MOV	R3,#0
		
		RET
		
INCE:	RET
		
DIST:	MOV	A,#01     		//Update display routine
		ACALL	COMNWRT    	//Reset display
		
		ACALL	DELAY2	
		MOV	A,R3   			//MSD first (hours)
		SWAP A
		ANL A, #0Fh        //remove second digit
		ADD A, #30h
		ACALL DATAWRT
		MOV	A,R3   			
		ANL A, #0Fh        //remove first digit
		ADD A, #30h
		ACALL DATAWRT
		
		ACALL	DELAY2	
		MOV	A,R2  			//MSD first (minutes)
		SWAP A
		ANL A, #0Fh         //remove second digit
		ADD A, #30h
		ACALL DATAWRT
		MOV	A,R2  			
		ANL A, #0Fh         //remove first digit
		ADD A, #30h
		ACALL DATAWRT
		
		ACALL	DELAY2	
		MOV	A,R1 			//MSD first (seconds)
		SWAP A
		ANL A, #0Fh         //remove second digit
		ADD A, #30h
		ACALL DATAWRT
		MOV	A,R1 			
		ANL A, #0Fh         //remove first digit
		ADD A, #30h
		ACALL DATAWRT
		
		RET
		
COMNWRT:                   	
		MOV	P1,A       	
		CLR	P2.0       	
		CLR	P2.1       	
		SETB	P2.2       	
		ACALL	DELAY1		
		CLR	P2.2       	
		RET
DATAWRT:                   	
		MOV	P1,A       	
		SETB	P2.0       	
		CLR	P2.1       	
		SETB	P2.2       	
		ACALL	DELAY1		
		CLR	P2.2       	
		RET

DELAY1:	MOV	R5,#30 			//Short delay
LP1: 	DJNZ	R5,LP1		
      	RET
		
DELAY2:	MOV	R5,#50 			//long delay 
HERE2:	MOV	R4,#50	
HERE: 	DJNZ	R4,HERE 		
     	DJNZ	R5,HERE2
      	RET		
	
		END
```