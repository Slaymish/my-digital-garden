---
{"dg-publish":true,"permalink":"/decoding-ic/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-04-2023
***

Is a [[EEEN Special Logic Function ICs\|EEEN Special Logic Function ICs]]

# Decoders

*activates an output that corresponds to a binary num on the input*

- N input - $2^N$ possible combination
- M outputs, with $M≤2^N$
- (Usually) only one O/P active at a time
- OUT can be active HI or LO

## Binary to Octal Decoder

*A three-line-to-8-line decoder*

- Aka '1-of-8' decoder
	- Only one output HI at a time ($O_0 \ - \ O_7$)

## 74ALS138 Decoder

- 1-of-8 decoder
- Active HI (One output LO at a time)
- Can connect 4 together to make a **1-of-32 decoder**


Other Decoders:
- 7442 BCD-to-decimal decoder
- BCD-to-7 segment decoder/driver
	- Whats used to display to 7segment display


