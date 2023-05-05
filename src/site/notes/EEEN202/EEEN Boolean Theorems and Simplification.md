---
{"dg-publish":true,"permalink":"/eeen-202/eeen-boolean-theorems-and-simplification/"}
---


# EEEN Boolean Theorems and Simplification

Related: 
Contents: [[EEEN202/EEEN MOC\|EEEN MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 10-03-2023
***

## Single Variable Theorems

$x*0 = 0$
$x*1 = x$
$x*x = x$
$x*not(x) = 0$
$x + 0 = x$
$x + 1 = 1$
$x + x = x$
$x + not(x) = 1$

## Multivariable Theorems

$x+y=y+x$
$x*y=y*x$
$x+(y+z)=(x+y)+z=x+y+z$
$x(yz)=(xy)z=xyz$
$x(y+z)=xy+xz$
$(w+x)(y+z)=wy+xy+wz+xz$
$x+xy=x$
$x+not(x)y=x+y$
$not(x)+xy=not(x)+y$

## DeMorgan's Theorems

- A NOR gate is equivalent to an AND gate with inverted inputs
- A NAND gate is equivalent to an OR gate with inverted inputs

# Combinatorial Logic

- Basic logic gate fns will combined to make the circuits
- The output depends only on the combination of logic levels at the input to the circuit

# Simplifying Logic Circuits

- Use sum-of products form
	- See ENGR 121/123 for more

[[simplifying logic circuits pract\|simplifying logic circuits pract]]


$Z = ABC + A*not(B)*(not(not(a)*not(c)))$
$Z=A(C+not(B))$


- Sometimes easiest way to to build the circuit straight from the truth table.



Problem:
Design a logic circuit that has three inputs, A, B, and C, whose output will be HIGH only when a majority of the inputs are HIGH.

| A   | B   | C   |     |
| --- | --- | --- | --- |
| 1   | 1   | 1   | 1   |
| 0   | 1   | 1   | 1   |
| 1   | 0   | 1   | 1   |
| 0   | 0   | 1   | 0   |
| 1   | 1   | 0   | 1   |
| 0   | 1   | 0   | 0   |
| 1   | 0   | 0   | 0   |
| 0   | 0   | 0   | 0   |

$(ABC)+(BC)+(AC)+(AB)$
$C(AB+A+B)+(AB)$
$C(A(B+1)+B)+(AB)$
$C(A+B)+(AB)$
$CA+BC+AB$
$A(B+C)+BC$


A---------
					|
					|
B----            |
		|or----|and---|
		|.                   
C----


B and C----------- or above ------ out


Can use [[EEEN202/EEEN K Maps\|EEEN K Maps]] instead

