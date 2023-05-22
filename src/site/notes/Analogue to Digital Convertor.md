---
{"dg-publish":true,"permalink":"/analogue-to-digital-convertor/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 19-05-2023
***

# Analogue to Digital Convertor

[[Feedback ADCs\|Feedback ADCs]]
	[[Staircase ADC\|Staircase ADC]]
	[[Tracking ADC\|Tracking ADC]]
	[[Flash ADC\|Flash ADC]]
	[[Voltage to frequency ADC\|Voltage to frequency ADC]]
	[[Sigma delta modulation\|Sigma delta modulation]]

## [[Multiplexing IC\|Multiplexing]]

- Multiple analog signals can be converted through time sharing of an ADC
- Multiplexing clock controls rate at which analog signals are switched to the ADC
- The ADC0808 can multiplex eight different analog inputs to one ADC

## General Info

- Will always have an error in conversion process
- Error decreases with number of bits used
- Conversion takes time

## Input Range

- Most cases - 0V
- Can be **unipolar** (0 to +x V)
- Or **bipolar** (-x V to +x V)

- number of bits + range will determine effective *resolution*
- Make sure it matches signal range

## Resolution

- Defined as the smallest change in the input voltage that will ensure a change the digital output by one code level

$$Resolution = \frac{Input\ Voltage\ Range}{2^{bits}-1}$$

### Resolution Error

$$=±0.5LSB = ± 0.5 * \frac{Input\ range}{(2^{bits}-1)}$$
The number of bits is often referred to as resolution of the convertor

## Steps

$$Steps=2^{bits}-1$$



****

## Practise

An 8-bit [[Analogue to Digital Convertor\|Analogue to Digital Convertor]] has an input range of 0-10 Volt. Calculate:
1. The resolution 
2. The quantisation error 
3. The convertor is constructed using a [[Successive Approximation (SAC) Convertor\|Successive Approximation (SAC) Convertor]]. Assume a clock cycle of $1 \mu s$. How long will one conversion take?






