---
{"dg-publish":true,"permalink":"/time-varying-signals/"}
---

Related: 
Contents: [[EEEN202/EEEN202 MOC\|EEEN202 MOC]]
[[UNI MOC\|UNI MOC]]
Hamish Burke || 22-05-2023
***

# A/D Samping Process

1. The input voltage is sampled by the system and converted into a *binary code*. Number of bits in code is determined by the A/D hardware and represents the accuracy with which the signal voltage can be represented
2. Sampling takes place at discrete points in time and sampling rate determines how accurately the signal can be represented on a time scale

<p align="center">
Increasing Sample rate = Increasing accuracy of signal voltage
</p>

## How Fast Do I Need to Sample?

- Double the signal frequency is the **bare minimum**

![300][SCR-20230522-r90.png]

If the [[Nyquist-Shannon theorem\|Nyquist-Shannon theorem]] is not satisfied there will be alias frequencies present in sampled data.

## Signal Change during the Sampling Process

How good a representation of the signal is the value that corresponds to the time stamp of the signal?

As A/D convertors take time to process, how much of an error will the changing signal during the conversion process introduce.

[[Sample and Hold devices\|Sample and Hold devices]]


