---
{"dg-publish":true,"permalink":"/staircase-adc/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 19-05-2023
***

# The ramp/staircase/counter [[Analogue to Digital Convertor\|Analogue to Digital Convertor]]

- Uses a binary up counter
- Feeds counter into [[Digital to Analog Conversion\|Digital to Analog Conversion]]
- DAC generates an analogue voltage representing the **binary count** of the counter

- This **increasing** analogue voltage is compared by [[Comparator\|Comparator]] to the analogue voltage to be measured ($V_{in}$) and the comparator will change state when $V_{DAC}>V_{in}$ 

- The comparator transition will **stop the counter** and also signal *End of Conversion*
- The counter value representing the binary conversion of the analogue voltage

![500][SCR-20230519-rad.png]

