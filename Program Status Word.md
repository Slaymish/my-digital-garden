---
dg-home: false
dg-publish: true
---
Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 07-05-2023
***

# Program Status Word

## Structure

| PSW.7 | PSW.6 | PSW.5 | PSW.4 | PSW.3 | PSW.2 | PSW.1 | PSW.0 |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| CY    | AC    | F0    | RS1   | RS0   | OV    | --    | P      |

| Bit | Symbol    | Flag name and desc                                |
| --- | --------- | ------------------------------------------------- |
| 7   | C (or CY) | Carry  - Used in arithmetic, logic/boolean ops    |
| 6   | AC        | Auxiliary Carry  - Useful only for BCD arithmetic |
| 5   | F0        | Flag 0; general purpose user flag                 |
| 4   | RS1       | Register bank selection bit 1                     |
| 3   | RS0       | Register bank selection bit 0                     |
| 2   | 0V        | Overflow - Used in arithmetic ops                 |
| 1   | --        | Reserved - Can be used as a general purpose flag  |
| 0   | P         | Parity - Set to 1 if A has odd number of ones, otherwise reset to 0                                                  |