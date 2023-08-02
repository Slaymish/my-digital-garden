---
dg-home: false
dg-publish: true
---
Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 20-03-2023
***
- Create a **Square Wave**
- Not a FF but shows a memory characteristic
- Accepts slow changing signals and produces a signal that transitions quickly

- Will not respond to an input until it exceeds the positive or negative going threshold
- Separation between the two threshold lvls
	- Device will 'remember' the last threshold exceeded until the input goes the opposite threshold

# Schmidt Trigger

![[Diagram 3.svg]]

# Standard Trigger

***

# Multivibrators

- Latches and FF's can be described as *[[EEEN Bistable Multivibrators\|bistable multivibrators]]*

## Monostable Multivibrator

*AKA a one-shot*
- Has only one stable state
	- 'default' or 'resting' state
- Used for simple timing applications
	- eg capacitors and resistors

## Astable Multivibrator

- Two equally stable out states
- Will constantly flip between those
- Ideal for a clock signal
- Not used in high-precision applications

**Applications:**
- Low end - Digital IC based clocks
- Medium - Crystal oscillator circuits
- Temperature controlled crystal oscillators, atomic clocks

## The 555 Timer

- Useful for lab (not in exam/test)
- Can be configured as a monostable or astable multivibrator





