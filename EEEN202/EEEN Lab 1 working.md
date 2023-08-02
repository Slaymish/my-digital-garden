---
dg-home: false
dg-publish: true
---

# EEEN Lab 1 - In Lab

Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 07-03-2023
***

## 4.1 Using the Design Station

- [x] Ensure that you are familiar with the functions and use of the design station and the breadboard. 
- [x] Use your digital multimeter in resistance function (alarm) and establish the contact pattern across the breadboard.  
  

## 4.2 Evaluating the 74HCT00, 74HCT02 and 74HCT04 Integrated Circuits

- [x] Establish a +5 V (red wire) bus on the outer perimeter rail of the breadboard and a  common rail (green wire) on the inner perimeter rail.
- [x] Place a 74HCT00 IC on the breadboard, and make the appropriate power connections. Connect Vext to +5 V on the  SDS, and the inputs for one of the four gates on the package to the logic level switches  (UP = HI). 
- [x] Connect the gate output to a logic indicator (ON = HI) with the logic  selector set to "TTL". 
- [x] Briefly confirm the operation of the gate in terms of LO's & HI's.
- [x] Repeat for each of the other two gates.  

## 4.3 Construction of Some Simple Logic Functions.

- [ ] Construct each of the logic function from Section 3.2.3 above using the appropriate logic gates. 
- [ ] Establish truth tables relating the inputs A and B to the output C for these circuits, using logic switches and LED logic indicators. (Note that "2/6 7404" means "two of the six gates in a 7404 chip", etc.) 
- [ ] sketch them in your log book with the inclusion of pin numbers. 
- [ ] Check that their operation agrees with your expected truth table.  
  

## 4.4 Construction of a One-Bit Half Adder Using Discrete Logic Gates.

- [ ] Construct this circuit that you designed in Section 3.2.6 using any of the three types of  logic gates. 
- [ ] Check the circuit operation.  
  

## 4.5 Implementing Logic Functions with a Multiplexer (MUX)

- [ ] Wire up the MUX with correct logic level on the input lines in order to make this 4:1 MUX function as (i) a NAND gate and (ii) an XOR gate.
- [ ] Check that it is operating correctly.  
  

## 4.6 Construction of a One-bit Half Adder Using a Multiplexer Solution

- [ ] The true convenience of using multiplexers is that we can use them in implementing arbitrary logic functions. 
- [ ] To demonstrate this capability, we will use the 74HCT153 dual

  
5  
  
4 line to 1 line MX to implement the one-bit adder.  
- 5V  
16 8  
9  
7  
Z  
Z  
B A (from logic switches)  
Carry  
Sum  
Vcc  
MX1  
MX2  
logic switch  
logic switch  
2 14  
13  
12  
11  
1  
15  
3  
4  
5  
6  
1 E  
I  
I1  
I2  
I3  
E  
I  
I1  
I2  
I3  
74HCT153  
  
Use your truth table to set the inputs (I0...I3) for CARRY & SUM to 1's (+5V) or 0's  
(common) by direct connection. With E1 & E2 set LO, check the operation of the adder.  
  
Investigate the effect of the ENABLE inputs (labelled E on the diagram) on the device  
operation. Note that the bubble symbols on the enable inputs indicate that they are  
active low.