---
dg-home: false
dg-publish: true
---
Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 25-03-2023
***

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

***

# Construction

- Counter has to count to 60
- Out 'stop' signal at 50

- Make using J-K FF's
- For stop signal, use [[EEEN Asynchronous Counters#^4e71a9\|Frequency division]]

## Mod

- See [[EEEN Asynchronous Counters#^8b1771\|MOD number]]
- MOD = 64
- $2^n=64$
- n = 6


So 6 J-K FF's to make it count to 64, as each FF is one bit

![[Diagram 12.svg]]






For stop signal, find the states of $Q_1-Q_6$  at 50 (110010)
Add all HI outputs into a NAND gate, out of that is stop signal

***

# For BCD Convertor

- 74HCT4511?

chrome-extension://gfbliohnnapiefjpjlpjnehglfpaknnc/pages/pdf_viewer.html?r=<https://assets.nexperia.com/documents/data-sheet/74HC_HCT393.pdf>


***

# Real Construction

Started using 74HCT393, changed to ==74HCT390== because that already counted in BCD. Plug HI's at state 50 into and gate plug that into ex or gate (74HCT86).

74HCT390: Dual decade ripple counter
<https://www.ti.com/lit/ds/symlink/cd74hct390.pdf?ts=1683174122181&ref_url=https%253A%252F%252Fwww.ti.com%252Fproduct%252Fzh-tw%252FCD74HCT390>

