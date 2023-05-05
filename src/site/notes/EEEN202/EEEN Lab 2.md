---
{"dg-publish":true,"permalink":"/eeen-202/eeen-lab-2/"}
---

Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 13-03-2023
***

# Pre-lab

[[EEEN202/EEEN Sequential Logic#^ea60f4\|EEEN Sequential Logic#^ea60f4]] - Link to notes
***
[[EEEN202/EEEN Lab 2 Report Task\|EEEN Lab 2 Report Task]]

## 2.1

*Show the construction of a basic NAND gate latch and use a truth table to show how the outputs depend on the inputs*

![SCR-20230313-e53 1.png](/img/user/SCR-20230313-e53%201.png)

| SET | CLEAR | OUT       |     | 
| --- | ----- | --------- | --- |
| 1   | 1     | No Change   |     |
| 0   | 1     | Q = 1     |  Latch is in SET   |
| 1   | 0     | Q = 0     |   Latch is in RESET  |
| 0   | 0     | Invalid |    Undesired state |

***

## 2.2

*Identify at least three different limitation of this basic S-C latch and show how each of these will be solved to produce a practical J-K flip-flop*

**Limitations:**
1. Unable to toggle its output state when both inputs are high. This can be solved in a J-K flip-flop by using the J and K inputs, which allow for toggling of the output state regardless of the input state.

2. Not a synchronous device (not tied to a clock). Solved in a J-K flip-flop by using a clock signal, which synchronizes the inputs and outputs

3. Sensitive to noise interference, which can cause unintended state changes. 

***

## 2.3

*The J-K flip flop has two inputs; show how this design can be modified to produce a D flip flop with a single data input*


**Truth table for a clocked J-K Flip Flop (triggers on PGT)**

| J   | K   | CLK | Q                    |
| --- | --- | --- | -------------------- |
| 0   | 0   | PGT | $Q_0$ (no change)    |
| 1   | 0   | PGT | 1                    |
| 0   | 1   | PGT | 0                    |
| 1   | 1   | PGT | $\neg Q_0$ (toggles) |

**Triggering on NGT**

| A   | B   | CLK | Q                    |
| --- | --- | --- | -------------------- |
| 0   | 0   | NGT | $Q_0$ (no change)    |
| 1   | 0   | NGT | 1                    |
| 0   | 1   | NGT | 0                    |
| 1   | 1   | NGT | $\neg Q_0$ (toggles) |

Can be implemented using a J-K flip flop by tying the J input to the K input through an inverter.
![brave_39Owi1AydM.png](/img/user/brave_39Owi1AydM.png)

***

# In Lab

## Section 3

### 3.1 The Basic SC Latch

NOR gate latch truth table:

| SET | CLEAR | OUTPUT    |
| --- | ----- | --------- |
| 0   | 0     | No change |
| 1   | 0     | Q = 1     |
| 0   | 1     | Q = 0     |
| 1   | 1     | Invalid   |

b) 
When I turn S to 1, $Q=1$ and $\neg Q = 0$
$Q$ and $\neg Q$ stay the same when S is returned to 0

c)
When I set C to 1, $Q=0$ and $\neg Q = 1$
No change again when set back to 0

d)
When both S and C are set to 1, $Q$ and $\neg Q$ go to zero. This is an invalid state

e)
For (SC) $11 \implies 10 \implies 00$, $Q=1$ and $\neg Q =0$
For (SC) $11 \implies 01 \implies 00$, $Q=0$ and $\neg Q =1$

f)
It doesn't give a reproducible result

***

### 3.4 The Edge-Triggered D FF

1. Does the operation of the RESET and SET lines depend upon the clock status?

The operation of the RESET and SET lines does not depend upon the clock status. They are asynchronous inputs, meaning that they can reset or set the flip-flop regardless of the clock's state.

3. What is the timing relation between Q and the CLK signal using the oscilloscope?

- Toggles on the PGT of the CLK
- CLK is **twice** the frequency as toggle

***

### 3.5 The JK Edge-Triggered FF

Truth table:

| J   | K   | CLK | Q                 |
| --- | --- | --- | ----------------- |
| 0   | 0   | NGT | $Q_0$ (no change) |
| 1   | 0   | NGT | 1                 |
| 0   | 1   | NGT | 0                 |
| 1   | 1   | NGT | $\neg Q_0$ (toggles)                  |

- It toggles on the negative edge transition of the CLK
- The CLK has twice the frequency as the toggle

Waveform Sketch:
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="300px" height="332px" viewBox="-0.5 -0.5 300 332" style="background-color: rgb(255, 255, 255);"><defs/><g><rect x="1" y="30" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 45px; margin-left: 2px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">J</div></div></div></foreignObject><text x="11" y="49" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">J</text></switch></g><rect x="1" y="90" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 105px; margin-left: 2px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">K</div></div></div></foreignObject><text x="11" y="109" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">K</text></switch></g><rect x="1" y="180" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 195px; margin-left: 2px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">CLK</div></div></div></foreignObject><text x="11" y="199" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">CLK</text></switch></g><rect x="1" y="260" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 275px; margin-left: 2px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">Q</div></div></div></foreignObject><text x="11" y="279" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">Q</text></switch></g><rect x="51" y="10" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 25px; margin-left: 52px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">1</div></div></div></foreignObject><text x="61" y="29" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">1</text></switch></g><rect x="51" y="50" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 65px; margin-left: 52px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">0</div></div></div></foreignObject><text x="61" y="69" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">0</text></switch></g><rect x="51" y="70" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 85px; margin-left: 52px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">1</div></div></div></foreignObject><text x="61" y="89" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">1</text></switch></g><rect x="51" y="110" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 125px; margin-left: 52px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">0</div></div></div></foreignObject><text x="61" y="129" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">0</text></switch></g><rect x="51" y="160" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 175px; margin-left: 52px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">1</div></div></div></foreignObject><text x="61" y="179" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">1</text></switch></g><rect x="51" y="200" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 215px; margin-left: 52px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">0</div></div></div></foreignObject><text x="61" y="219" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">0</text></switch></g><rect x="51" y="240" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 255px; margin-left: 52px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">1</div></div></div></foreignObject><text x="61" y="259" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">1</text></switch></g><rect x="51" y="280" width="20" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 18px; height: 1px; padding-top: 295px; margin-left: 52px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">0</div></div></div></foreignObject><text x="61" y="299" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">0</text></switch></g><path d="M 91 220 L 131 220 L 131 180 L 171 180 L 171 220 L 211 220 L 211 180 L 251 180 L 251 220 L 284.63 220" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 289.88 220 L 282.88 223.5 L 284.63 220 L 282.88 216.5 Z" fill="rgb(0, 0, 0)" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="all"/><path d="M 131 330 L 131 0" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" stroke-dasharray="3 3" pointer-events="stroke"/><path d="M 171 330 L 171 0" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" stroke-dasharray="3 3" pointer-events="stroke"/><path d="M 211 330 L 211 0" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" stroke-dasharray="3 3" pointer-events="stroke"/><path d="M 251 330 L 251 0" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" stroke-dasharray="3 3" pointer-events="stroke"/><path d="M 81 25 L 284.63 25" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 289.88 25 L 282.88 28.5 L 284.63 25 L 282.88 21.5 Z" fill="rgb(0, 0, 0)" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="all"/><path d="M 81 84.5 L 284.63 84.98" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 289.88 85 L 282.87 88.48 L 284.63 84.98 L 282.89 81.48 Z" fill="rgb(0, 0, 0)" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="all"/><path d="M 91 294 L 131 294 L 131 254 L 171 254 L 171 294 L 211 294 L 211 270 L 211 254 L 251 254 L 251 294 L 284.63 294" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 289.88 294 L 282.88 297.5 L 284.63 294 L 282.88 290.5 Z" fill="rgb(0, 0, 0)" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="all"/></g><switch><g requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"/><a transform="translate(0,-5)" xlink:href="https://www.diagrams.net/doc/faq/svg-export-text-problems" target="_blank"><text text-anchor="middle" font-size="10px" x="50%" y="100%">Text is not SVG - cannot display</text></a></switch></svg>
