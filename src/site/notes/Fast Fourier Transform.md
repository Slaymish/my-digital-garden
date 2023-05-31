---
{"dg-publish":true,"permalink":"/fast-fourier-transform/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 31-05-2023
***

# Fast-Fourier Transform (FFT)

## Polynomial Multiplication

$$A(x) = x^2 + 3x +2,B(x) =. 2x^2+1$$
$$C(x)=A(x)*B(x)$$

- When doing Polynomial Multiplication, **we just care about the coefficients**
- Re-sort so lowest power is first

$A=2+3x+x^2$
$B=1+0x+2x^2$
$C=2+3x+5x^2+6x^3+2x^4$

$A=[2,3,1]$
$B=[1,0,2]$
$C=[2,3,5,6,2]$


$C[k]$ is coefficient of $k^{th}$ degree term of polynomial $C(x)$

### Complexity

- $n$ is the highest degree of the polynomials $A(x)$ and $B(x)$
$$O(n^2)$$

### General Rule

$$C(x)=A(x)B(x)=\sum ^{2n}_{i=0}c_ix^i=c_0+c_1+c_2x^2+...+c_{2n}x^{2n}$$

***

## Point Representation

A polynomial of degree n can be uniquely represented by n+1 points

EG: 2 points determine a line, 3 points determine a parabola


- Amount of points correspond to the number of coefficients

- Can reconstruct coefficients of P(x) from n+1 values
	- Requires $O(n^2)$ 
- called **Value Representation** of a polynomial

![350][SCR-20230531-te7.png]

- Points chosen by ourselves

## Pointwise Multiplication

$$C(x_i)=A(x_i)B(x_i)$$
- Need $K=2n+1$ points to reconstruct a polynomial of degree 2n

### Complexity

$$O(n^2)$$

***

## To Make Faster!

for eg $P(x)=x^2$

The value of one point immediately implies the value of another
$$P(x)=P(-x)$$

for $P(x)=x^3$
$$P(x)=-P(-x)$$

- For above odd **and** even, only need to evaluate half of the points from which we immediately know the value of the respective negative points

## Extend Idea

