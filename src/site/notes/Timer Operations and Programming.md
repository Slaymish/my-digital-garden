---
{"dg-publish":true,"permalink":"/timer-operations-and-programming/"}
---

Related: 
Contents: [[EEEN202/EEEN202 MOC\|EEEN202 MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

[[The 8051 Instruction Set\|The 8051 Instruction Set]]

# Timer Operations

Timers are used for:
- Interval timing
	- Timer is programmed to overflow at a regular interval and
		- Set the timer overflow flag or
		- Generate an interrupt
	- Can be used to generate waveforms
- Event counting
	- used to **count** num of occurrences of an event
	- An event is any external stimulus that provides a **high-to-low** transition at the selected input pin

## Timer Mode1

*We'll only consider this mode*

- 16-bit timer

Counts up from the preloaded value **THx**,**TLx** and when it reached the max count value it sets the flat TFx and makes an interrupt (if enabled). 

Can 'poll' the the TFx flag to determine when the max count has been reached

### Basic Setup

For TMOD mnemonic:
- To set to mode one, set M01 to 1
- Set GATE0 to 0

## Programming Sequence

- For timers 0 and 1

1. Check input clock
2. Select operating mode in TMOD
3. Write starting value for count up sequence into the associated count registers (TL0,TL1,TH0 and TH1)
4. (optional) enable timer interrupt (ET0 or ET1 in IE) and global interrupts (EA in IE)
5. Set the appropriate control bits, and turn on timer (TR0 or TR1 in TCON)


To detect when timer overflow, you can:

- Poll the timer overflow bit
- Or enable the timer overflow interrupt

## Timer Modes

<https://www.engineersgarage.com/timers-8051-timer-programming/>

**(i) Mode 0 : 13-bit Timer**

Mode 0 is a 13 bit Timer mode and uses 8 bits of high byte and 5 bit prescaler of low byte. The value that the Timer can update in mode0 is from 0000H to 1FFFH. The 5 bits of lower byte append with the bits of higher byte. The Timer rolls over from 1FFFH to 0000H to raise the Timer flag.

**(ii) Mode 1 : 16-bit Timer**

Mode1 is one of the most commonly used Timer modes. It allows all 16 bits to be used for the Timer and so it allows values to vary from 0000H to FFFFH.


