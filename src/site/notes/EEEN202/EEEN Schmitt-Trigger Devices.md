---
{"dg-publish":true,"permalink":"/eeen-202/eeen-schmitt-trigger-devices/"}
---

Related: 
Contents: [[EEEN202/EEEN202 MOC\|EEEN202 MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 20-03-2023
***
- Create a **Square Wave**
- Not a FF but shows a memory characteristic
- Accepts slow changing signals and produces a signal that transitions quickly

- Will not respond to an input until it exceeds the positive or negative going threshold
- Separation between the two threshold lvls
	- Device will 'remember' the last threshold exceeded until the input goes the opposite threshold

# Schmidt Trigger

<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="391px" height="399px" viewBox="-0.5 -0.5 391 399" style="background-color: rgb(255, 255, 255);"><defs/><g><path d="M 124 0 L 286 90 L 124 180 Z" fill="rgb(255, 255, 255)" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="all"/><path d="M 70 90 L 124 90 M 286 90 L 340 90 M 151 105 L 194.2 105 C 197.06 105 199.81 103.74 201.84 101.49 C 203.86 99.23 205 96.18 205 93 L 205 87 C 205 83.82 206.14 80.77 208.16 78.51 C 210.19 76.26 212.94 75 215.8 75 L 218.5 75 L 175.3 75 C 172.44 75 169.69 76.26 167.66 78.51 C 165.64 80.77 164.5 83.82 164.5 87 L 164.5 93 C 164.5 99.63 159.66 105 153.7 105 Z" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="all"/><rect x="0" y="75" width="60" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 58px; height: 1px; padding-top: 90px; margin-left: 1px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">A</div></div></div></foreignObject><text x="30" y="94" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">A</text></switch></g><rect x="330" y="75" width="60" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 58px; height: 1px; padding-top: 90px; margin-left: 331px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">X</div></div></div></foreignObject><text x="360" y="94" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">X</text></switch></g><path d="M 70 267.5 Q 120 267.5 120 238.75 Q 120 210 195 210 Q 270 210 270 240 Q 270 270 333.63 270" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 338.88 270 L 331.88 273.5 L 333.63 270 L 331.88 266.5 Z" fill="rgb(0, 0, 0)" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="all"/><rect x="10" y="260" width="60" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 58px; height: 1px; padding-top: 275px; margin-left: 11px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">A</div></div></div></foreignObject><text x="40" y="279" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">A</text></switch></g><rect x="10" y="365" width="60" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 58px; height: 1px; padding-top: 380px; margin-left: 11px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: Helvetica; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;">X</div></div></div></foreignObject><text x="40" y="384" fill="rgb(0, 0, 0)" font-family="Helvetica" font-size="12px" text-anchor="middle">X</text></switch></g><path d="M 70 360 L 70 350 L 120 350 L 120 390 L 270 390 L 270 350 L 340 350 L 363.63 350" fill="none" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 368.88 350 L 361.88 353.5 L 363.63 350 L 361.88 346.5 Z" fill="rgb(0, 0, 0)" stroke="rgb(0, 0, 0)" stroke-miterlimit="10" pointer-events="all"/></g><switch><g requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"/><a transform="translate(0,-5)" xlink:href="https://www.diagrams.net/doc/faq/svg-export-text-problems" target="_blank"><text text-anchor="middle" font-size="10px" x="50%" y="100%">Text is not SVG - cannot display</text></a></switch></svg>

# Standard Trigger

***

# Multivibrators

- Latches and FF's can be described as *[[EEEN202/EEEN Bistable Multivibrators\|bistable multivibrators]]*

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





