---
{"dg-publish":true,"permalink":"/microcontroller-design-exercise/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 19-05-2023
***

# [[Successive Approximation (SAC) Convertor\|Successive Approximation (SAC) Convertor]]

- Doing it all in C!
- Will start with buggy code
- Got 2 weeks to do it
- will probably use the [[ADC0804 8-bit SAC\|ADC0804 8-bit SAC]]

- potentiometer 451t0


![300][SCR-20230523-f0b.png]

## Timing Comparisons

| V     | Staircase                   | Successive Approx |
| ----- | --------------------------- | ----------------- |
| 4.92  | 252 (goes blank any higher) |                   |
| 4     | 227                         |                   |
| 2     | 177                         |                   |
| 0     | 129                         |                   |
| -2    | 77                          |                   |
| -4    | 28                          |                   |
| -4.92 | 3 (drops to 1 at any lower) |                   |

We multiplied the returned test_val is by 0.0196
- Connect up to a multimeter, voltages>5V (measured on multimeter) wasn't getting displayed on lcd display


