---
{"dg-publish":true,"permalink":"/arithmetic-coding/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 31-05-2023
***

# Arithmetic Coding

- Still based on the frequency of symbols
- Though reads as stream (whole sequence) instead of [[Huffman coding\|Huffman coding]] or similar
- Uses probability of a **whole sequence**
- Represents it as a [[Binary Fraction\|Binary Fraction]]

## Example

```
X = {A,B,C}
0.5, 0.25, 0.25

S = AAB 

1. Find probability of whole sequence
2. 0.5*0.5*0.25 = 1/16 <- probability of S
```

## Intervals as Bit-strings

- The interval corresponding to $n$-bits has width $\frac {1}{2^n}$
- To specify interval of size $\alpha$, we need about $log_2 \frac {1}{\alpha}$ bits

```
EG: if a = 1/8
we need log2 (1/a) = 3bits
```

## Sending Interval

- To send a string, **recursively** partition up the interval `[0,1]` into segments

## On the Fly Encoding

- transmitting bbba
- aim is to find the largest interval (kinda like) [[String Search\|String Search]]
- Goes letter by letter, appending more to the current probabilities code when there's a new partition

***

# Best Partitioning Scheme

- Suppose scheme gives string $S$ an interval of size $\alpha _s$
- is going to require $log_2 \frac {1}{\alpha _s}$ bits
- Recursive 'chain rule' of probabilities
	- Machine learning

## Expected Message Length

$$\sum _S P_S log_2 \frac {1}{\alpha _S}$$

