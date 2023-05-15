---
{"dg-publish":true,"permalink":"/address-control/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

# Address Control

## ORG

- The ORG directive is used to set the location counter

```
ORG <expression>
```

### Example

```
ORG 80H // set location counter to 80H
```

To reserve one byte memory space at locations seconds and minutes in the data segment:

```
		DSEG // data segment
		ORG 30H 
SECONDS:DS 1
MINUTES:DS 1
```

## END

- Indicated the end of the source file
- Informs assembler where to stop assembling the program
- Required in every source file