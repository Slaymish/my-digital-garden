---
{"dg-publish":true,"permalink":"/symbol-definition/"}
---

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-05-2023
***

# Symbol Definition

- Assigns a symbolic name to an *expression* or a *register*
- By equating the symbol to a value, the user only needs change it once at the directive statement

## EQU and SET

```
Symbol EQU <expression>
Symbol EQU <register>
Symbol SET <expression>
Symbol SET <register>
```

- Similar to `#define` macro in [[NWEN241/NWEN C Fundamentals\|C]]
- Expression can includes math operations

### Example

- Equate hardcodes it, SET allow it to be updated

```
COUNT EQU R3 // equate to a register
TOTAL EQU 200 // equate to a constant

AVERG SET TOTAL/5 
TABLE EQU 10
VALUE SET TABLE*TABLE
```

## CODE and DATA

```
Symbol BIT <bit address>
Symbol CODE <code address>
Symbol DATA <data address>
```

### Example

```
Act_bit BIT 2H // use bit location 2H as Act_bit
Port2 DATA A0H // A special function register, P2
```

## DB (Define Byte)

- Initialises code memory with a byte value

```
<label>: DB <expression>,<expression>,...
```

### Example

String of characters will be stored as ASCII bytes starting from location 200H

```
CSEG AT 200H
MSG: DB 'Please enter your password', 0

ARRAY: DB 10H,20H,30H,40H,50H
```

DB directive can only be declared in a **code segment**

## DW (define word)

- Initialises the code memory with a double byte or 16-bit word
- Only can be used in the code segment

```
<label>: DW <expression>,<expression>,...
```

## DD (define Double word)

- Initialises the code memory with a double word or 32-bit data word
- Only can be used in the code segment

```
ADDRL DD 820056EFH,10203040H
```

## DS (define storage)

- Reserves a specified number of bytes in the current segment

```
<label>: DS <expression>
```

- Can't contain forwards references

