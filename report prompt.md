# Report Prompt

## The Clock

- Use the signal generator on the design station
- Set to a square wave with frequency = 2Hz

## [[Odometer (15%)]]

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

## Odometer Display

- Two seven-segment displays
- From odometer output

## Motor Control (10%)

- Once rover travelled 50m, should generate a stop signal
- Should stop the CLK signal 
- Generate a 'battery charged' signal that will enable CLK again
	- Off counter?

## [[Grey Code Generator (15%)]]

- Generate a 3-bit gray code pattern
- Should contain a direction bit D that'll allow it to count UP (D=1) or DOWN (D=0) in grey code.
	- Rest of system will assume only forwards
- G2G1G0
- Only one bit changes at a time
- Minimises risk of errors
- *D FF's and MUXes might be easiest*

## System Integration and Testing (10%)

- Ensure that every sub-system is working correctly *as* you construct them
