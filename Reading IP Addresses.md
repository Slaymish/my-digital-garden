---
dg-home: false
dg-publish: true
---
Related: [[NWEN241 MOC]]
Contents: [[NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 27-07-2023
***

# Reading [[Internet Protocol]] Addresses

- 32 bits long
- Divided into 4 8-bit segments (**Octets**)
- Decimals mean nothing

## Example

Using [[NWEN243 Project 1]] IP address

Public IP: 52.23.167.1

```
00110100.00010111.10100111.00000001
```

## Slash Notation

`192.168.1.0/24`

The `/24` means the first 24 **bits** are the network address

That means that you can use a max of 256 (2^8) addresses 
- -1 for the .0
- -1 for the router address (reserved for router)
- So **254**


