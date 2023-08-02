---
dg-home: false
dg-publish: true
---
Related: [[NWEN241 MOC]]
Contents: [[NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 10-07-2023
***

# Representing Data as Bits

For cloud computing, everything has to be turned into bits!

- Numbers
- Unicode/ASCII for text
- Images
	- Using a bitmap
		- 24bits/pixel
		- Each color is 1byte (0-255)
	- JPEG is a more effiecient way
 - Audio
	 - [[Sample and Hold devices]]
	 - [[Analogue to Digital Convertor]]
- Video
	- Sequence of images
	- Can **only** transmit things that change

## Modulation

Process of *transforming bits of data to electric/electromagnetic signals* to be propagated over a physical channel is called **modulation**

Reverse process is call **demodulation**


Can encode information into the *frequency, phase and amplitude* of the wave

### Network Adaptor

- Device responsible for modulation/demodulation (and synchronisation)
- Aka modem, network interface controller (NIC)

## Bandwidth/Throughput

Max 'rate' at which information *can* be transferred over a channel

- Measured in bps (Kbps, Mbps, Gbps, Tbps)
- Throughput is how much data *is* transferred over a channel

Can increase throughput by:
- Increasing clock rate
- Increasing num bits/symbol

Why limited throughput:
- [[Signal Degredation]]
- Increases the amount of bit errors...
- [[Propagation Delay (Link Latency)]]

## Transmission Medium

### Guided

- Ethernet cable, coaxial cable etc

### Unguided

- air, atmosphere
- infrared, wifi etc

