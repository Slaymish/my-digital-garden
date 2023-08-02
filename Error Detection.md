---
dg-home: false
dg-publish: true
---
Related: [[NWEN241 MOC]]
Contents: [[NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 13-07-2023
***

# Error Detection

In the [[Data Link Layer]]

- Can use a [[Checksum]]
	- Not used in [[Data Link Layer]]

## CRC

- What is actually used
- [[Cyclic Redundancy Check]]

## Parity Check

- Similar idea to a [[Checksum]]
- Make num of nums in data even or odd
- Have a **parity bit** at end of data, indicating where the data is even/odd parity
- Get receiver to count num of ones (including parity), and check if it makes the parity bit

## Forward Error Correction (FEC)

- A type of *code*
	- Of how the data was transmitted

- Error correction requires a great num of redundant bits to deal with same range of errors as a *code* that only detects errors