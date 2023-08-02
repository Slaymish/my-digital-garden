---
dg-home: false
dg-publish: true
---
Related: 
Contents: [[EEEN202 MOC]]
[[UNI MOC]]
Hamish Burke || 15-05-2023
***

# Segment Control

A contiguous block of code/data memory is referred to as a segment
- EG
	- A function definition (code memory)
	- An array (data memory)

## Absolute Segment

- Means a fixed memory segment
- Created by CSEG and DSEG directives
- Final location is known at compile time

Format of this directive:

```
CSEG AT <address> // defines an absolute code segment
DSEG AT <address> // defines an adsolute data segment
```

```
// select code segment and set the starting address to 0300H
CSEG AT 0300H 

// Select data segment and set starting address to 0400H
DSEG AT 0400H
```
