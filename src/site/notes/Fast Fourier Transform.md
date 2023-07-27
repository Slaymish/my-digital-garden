---
{"dg-publish":true,"permalink":"/fast-fourier-transform/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
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

# To Make Faster!

for eg $P(x)=x^2$

The value of one point immediately implies the value of another
$$P(x)=P(-x)$$

for $P(x)=x^3$
$$P(x)=-P(-x)$$

- For above odd **and** even, only need to evaluate half of the points from which we immediately know the value of the respective negative points

## Extend Idea

- So it works with a more general polynomial

$P(x)=3x^6+4x^5+2x^4-7x^3-8x^2+6x+1$

- Split $P(x)$ between even/odd powers

$P(x)=(3x^6+2x^4-8x^2+1)+(4x^5-7x^3+6x)$
$P(x)=(3x^6+2x^4-8x^2+1)+x(4x^4-7x^2+6)$ // extract x from odd


$P_{even}(x^2)=P_{even}(-x^2)$

$P_{odd}(x^2)=4(x^2)^2-7(x^2)+6$


***

$$P(x_i)=P_{even}(x_i^2)+x_iP_{odd}(x_i^2)$$
$$P(-x_i)=P_{even}(x_i^2)-x_iP_{odd}(x_i^2)$$

- Only need to evaluate $P_{even}$ and $P_{odd}$ at $n/2$ points
- Divide and conquer algorithm ([[Fast Fourier Transform\|Fast Fourier Transform]])
- $O(NlogN)$ recursive algorithm

**Further split each side to smaller polynomials**

## Example

$P(x)=-7x^3-8x^2+6x+1$

- Need degree (which is 3) + 1 = 4 points for this cubic polynomial
- These points are **tow pairs** of positive/negative points
- For $P(x):x_1,-x_1,x_2,-x_2$

- $P(x_i)=P_{even}(x_i^2)+x_iP_{odd}(x_i^2)$

Further split up those two, now will only require one point for evaluation:
$x^2=-x^2$
$x_1^4=1$

We need to use non real numbers
- As need to choose a number that, when squared, returns -1

### The 4th Roots of Unity

$x^4=1$ has four solutions

## General Solution

- If $P(x)$ has degree 5, need $n>6$ points. Let $n=8$ (power of 2)
- Solution for $x_1^8=1$ called the **8th roots of unity**

- 
- 
***

# Complex Numbers

$x=x.Re+i*x.Im$ 
- Re = real part
- Im = imaginary part)

## Exponential Operation

$$e^{a+b*i}=e^a*e^{b*i}=e^a*(\cos b + i*\sin b) = e^a\cos b + e^a\sin b*i$$



Tested on basic idea of utilising complex numbers in FFT

# Nth Roots of Unity

- Property that they are positively and negatively paired

$$z^n=1=1+i*0$$
Let $W=e^{2\pi i/n}=cos(\frac {2 \pi }{n})+i*sin(\frac {2\pi }{n}))$

$$W^k=e^{k*2\pi i/n}$$
$k=0,1,...,n-1$


When squaring these, it resamples the points around a [[Unit circle\|Unit circle]]
- Those are still ±pairs !!


***

![SCR-20230601-i8b.png](/img/user/SCR-20230601-i8b.png)

# Pseudocode

![SCR-20230601-ib4.png](/img/user/SCR-20230601-ib4.png)

- Making it recursive decreased the time complexity
	- Cus split up problem, only have to evaluate one point now
- From $O(n^2)$ to $O(nlogn)$ n = closest power of 2 to degree of polynomial


![SCR-20230601-ien.png](/img/user/SCR-20230601-ien.png)

FFF = $O(nLogn)$ 
n = closest power of 2 to degree of polynomial

## Interpolation

Can map and store each point value in matrix
Called a [[Discrete Fourier Transform matrix\|Discrete Fourier Transform matrix]] (DFT)
Then take the inverse of DFT and multiply by matrix containing all of $P(W^n)$
This is equal to a **matrix of the coefficients**
Inverse FFT (from values to coeefs)
	If we let $W'=\frac {1}{n}e^{\frac {-2\pi i}{n}}$



