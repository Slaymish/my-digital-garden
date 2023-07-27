---
{"dg-publish":true,"permalink":"/fft/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP261 MOC\|COMP261 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 01-06-2023
***

Below is the same notes as [[Fast Fourier Transform\|Fast Fourier Transform]], but reformatted

# 1. Polynomial Multiplication

Let's take two polynomials $A(x) = x^2 + 3x +2$ and $B(x) = 2x^2+1$. When we multiply these two polynomials, i.e., $C(x)=A(x)*B(x)$, we **only care about the coefficients**. Thus, we reorder the polynomials to start with the lowest power term first:

$A=2+3x+x^2$

$B=1+0x+2x^2$

Resulting in:

$C=2+3x+5x^2+6x^3+2x^4$

In terms of coefficient arrays, this looks like:

$A=[2,3,1]$

$B=[1,0,2]$

$C=[2,3,5,6,2]$

Where $C[k]$ is the coefficient of the $k^{th}$ degree term of polynomial $C(x)$. For two polynomials $A(x)$ and $B(x)$, each with a highest degree of $n$, the time complexity of this multiplication is $O(n^2)$.

This general rule applies for polynomial multiplication:

$$C(x)=A(x)B(x)=\sum _{i=0}^{2n}​c_i​x_i=c_0​+c_1​+c_2​x^2+...+c_{2n}​x^{2n}$$

## 2. Point Representation

A polynomial of degree $n$ can be uniquely represented by $n+1$ points. For instance, 2 points determine a line, and 3 points determine a parabola. This number of points corresponds to the number of coefficients. Hence, we can reconstruct the coefficients of a polynomial $P(x)$ from $n+1$ values, which takes $O(n^2)$ time. This is referred to as the **Value Representation** of a polynomial.

When performing pointwise multiplication, we need $K=2n+1$ points to reconstruct a polynomial of degree 2n. This operation also has a time complexity of $O(n^2)$.

## 3. FFT: A Faster Approach

To speed up these operations, we can leverage certain properties of polynomials and complex numbers.

For example, for a polynomial $P(x)=x^2$, the value of one point immediately implies the value of another, i.e., $P(x)=P(-x)$. For $P(x)=x^3$, we have $P(x)=-P(-x)$. In these cases, we only need to evaluate half of the points, from which we immediately know the value of the respective negative points.

We can extend this idea to more general polynomials by splitting $P(x)$ between even/odd powers, evaluating $P_{even}$ and $P_{odd}$ at $n/2$ points. This divide and conquer algorithm forms the basis of the Fast Fourier Transform (FFT), reducing the time complexity to $O(NlogN)$.

To reconstruct a polynomial of higher degree, we need more points. These points will be pairs of positive/negative points. For the general solution, we use a complex number, often referred to as the **Nth roots of unity**, which gives us the needed points.

## 4. Complex Numbers and Nth Roots of Unity

Complex numbers are a crucial part of FFT. Represented as $x=x.Re+i*x.Im$ (where Re is the real part and Im is the imaginary part), they have a distinct property in the exponential operation:

$$e^{a+b*i}=e^a*a^{b*i}=e^a*(\cos b + i*\sin b) = e^a\cos b + e^a\sin b*i$$

We leverage this property when utilising the **Nth roots of unity**, represented as $z^n=1=1+i_0$. Let's say $W=e^{2\pi i/n}=cos(\frac {2 \pi }{n})+i_sin(\frac {2\pi }{n})$, then

$$W^k=e^{k*2\pi i/n} for \ k=0,1,..,n-1$$

This allows us to resample points around a unit circle, maintaining ±pairs, which is beneficial in FFT.

## 5. Interpolation and Inverse FFT

We can map and store each point value in a matrix, known as a Discrete Fourier Transform matrix (DFT). By taking the inverse of the DFT and multiplying it by the matrix containing all of $P(W^n)$, we obtain a matrix of coefficients, signifying the Inverse FFT (from values to coefficients). If we let $W'=\frac {1}{n}e^{\frac {-2\pi i}{n}}$, we can perform this operation more efficiently.

Overall, implementing FFT results in a significant decrease in time complexity from $O(n^2)$ to $O(nlogn)$, where $n$ is the closest power of 2 to the degree of the polynomial.
