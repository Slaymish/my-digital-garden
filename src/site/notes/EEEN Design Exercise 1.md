---
{"dg-home":false,"dg-publish":true,"permalink":"/eeen-design-exercise-1/","dgPassFrontmatter":true}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 25-03-2023
***
For labs week 5&6

![550][SCR-20230325-pnj.png]

Report due 5th May
All lab work done *before* mid trimester break


***

# Week 5

## The Clock
- Use the signal generator on the design station
- Set to a square wave with frequency = 2Hz

## Odometer (15%)
- Measures every time wheel does a **full rotation**
- Rover will travel **1 meter** for every full revolution
- Count up to a total distance of 64 (or 60) meters of travel
- Though limit travel to 50m (to recharge batteries)
	- Output a stop signal after 50m
	- Count either pulses from the CLK or use OUT from the grey code
		- Starts Motor control system
			- Shuts down CLK
- Out
	- Binary encoded decimal (for display) (BCD)
		- Either build binary-BCD convertor
		- Or get an IC that does this
		- Or use a counter that directly gives a BCD output

## Odometer display
- Two seven-segment displays
- From odometer output

## Motor Control (10%)
- Once rover travelled 50m, should generate a stop signal
- Should stop the CLK signal 
- Generate a 'battery charged' signal that will enable CLK again
	- Off counter?


***

# Week 6

## Grey Code Generator (15%)
- Generate a 3-bit gray code pattern
- Should contain a direction bit D that'll allow it to count UP (D=1) or DOWN (D=0) in grey code.
	- Rest of system will assume only forwards
- G2G1G0
- Only one bit changes at a time
- Minimises risk of errors

## System Integration and Testing (10%)
- Ensure that every sub-system is working correctly *as* you construct them

## Report (40%)
- Due 5th May
- a description of the design process and method for each of the sub-systems
- A short statement that you have tested it and that it works as desired. If not working correctly, it should be pointed out and discussed
- You should submit the circuit diagrams for each of the sub-systems
	- including pin nums, ic's etc
- No longer than 4 pages (A4) in 12pt font (excluding circuit diagrams)
![400][SCR-20230325-qam.png]


***


# Design Hints
- Draw the state transition diagram for these transitions
- You should base your design on D or J-K FF as the sequential elements, and implement the combinatorial logic either in logic gates or MUX's
- Simplify where possible in order to yield the simplest circuit
- Decide which of the solutions (D or J-J and logic gates or MUX's) would be simplest to implement, build, and test this circuit






