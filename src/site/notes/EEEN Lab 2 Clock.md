---
{"dg-publish":true,"permalink":"/eeen-lab-2-clock/"}
---

Related: #Microcontrollers [[clock1.a51\|clock1.a51]]
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-05-2023
***

# Additional Questions

1) How can we speed up the process of verifying that the clock is counting correctly?  
2) If you place an oscilloscope probe on Port2-bit3, you will see a square wave. You will notice that the widths are not exactly 1 second. How can we correct this?  
3) Try and change the code to make the clock start at a different time.

***

1.  In wait, duplicate  `ACALL INCT`. This will increment the count twice every repeat of wait. This will make the count increase 2x as fast as normally. If you want to be faster, you could duplicate this line multiple times. If you wanted to test boundary cases, I would set the initial values of registers 1,2, and 3 to be closer to the values of the desired reset state. You can do this by changing the data value in `MOV Rx, #data` on lines 3-5. For example if you we're trying to test *minutes* reset, you could change `MOV R2,#0` to `MOV R2,#59`. Then you will only have to wait one minute.
<br>
2.  The widths of the square wave on Port2-bit3 are not exactly 1 second because the timer is not being configured to run at the correct frequency. To correct this, you can change the value of the TMOD register. If you are using a 16 MHz crystal oscillator, you would need to set the TMOD register to 0x02. For example:

	```assembly
	MOV TMOD,#0x02
	```

<br>
4.  Same as one of my options for Q1, to change the time at which the clock starts, you can change the values of the R1, R2, and R3 registers. The R1 register stores the seconds, the R2 register stores the minutes, and the R3 register stores the hours. These can be changed on lines 3-5 at the top of the file. For example, if you wanted the clock to start at 00:10:50, I would change the code to:

	```assembly
	MOV R1, #50 // seconds
	MOV R2, #10 // minutes
	MOV R3, #0 // hours
	```