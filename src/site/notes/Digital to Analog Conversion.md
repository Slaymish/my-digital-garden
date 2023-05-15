---
{"dg-publish":true,"permalink":"/digital-to-analog-conversion/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

# Conversion Process

1. Digital code is converted to a **voltage or current** proportional to the digital code
2. Voltage reference used to determine the full scale O/P
3. Analog O/P = K x digital I/P
4. 'Pseudo analog' as O/P cannot take on continuous values
5. Dipolar DACS: Use 2's compliment to represent negative voltages

## Four-bit DAC with Voltage Output

![SCR-20230515-ugx.png](/img/user/SCR-20230515-ugx.png)

A 5-bit DAC has a current O/P. For a digital I/P of 10100 and O/P current of 10 mA is produced. What is:

1. $I_{out}$ for a digiital I/P of 11101
2. The full scale O/P?

1) 
$10100 = 20$
$K=10mA/20 = 0.5mA$
So for 11101,
$1 + 4 + 8 + 16 = 29$
$29*0.5mA = 14.5mA$ (the current O/P for 11101)

2) 
$11111 = 31$
$31*0.5 = 15.5mA$ (the full scale O/P)


***

<h1 align="center">
Resolution
</h1>


- Difference in O/P voltage cause by a single code bit change on the I/P

$$Resolution = \frac{Full \ scale \ analog \ output}{2^2-1}=K$$

<h2 align="center">

Percentage Resolution

</h2>

$$\% res = \frac{Step \ step}{Full scale *100\%}$$

***

## Precision

Depends on:

1) Precision of the resistors. Can be made accurate by *trimming*

2) Precision of the I/P voltages. Use digital signals to select a precision voltage supply

***

# DAC IC

*DAC8562*

## Features

- 12-bit DAC
- Single +5 volt operation
- 4.095V Full Scale

***

# Applications

- Control
	- use a digital computer output to adjust motor speed
- Automatic testing
	- Computer generated signals to test analog circuitry
- Signal reconstruction
	- Restoring an analog signal after it ahas been converted to digital. 
		- Audio CD systems
		- audio/video recording
- Direct digital synthesis


***

# Generating a Sinusoidal Waveform (sin wave)

- Command D/A application

Will use:
- a clock
- a counter driven by the clock
- a sine ROM
- An ADC driven by the [[ROM\|ROM]] O/P
- A low pass filter to reduce distortion or other signal shaping circuitry

![450][SCR-20230515-v6s.png]

# Pulse Width Modulation (PWM) Dac

- a single digital output can be used to generate a waveform
- done by low pass filtering a PWM output

