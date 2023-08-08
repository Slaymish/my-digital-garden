---
{"dg-publish":true,"permalink":"/tcp-transmission-control-protocol/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# TCP

- Protocol for [[End-to-End Communication\|End-to-End Communication]] layer
- Requires acknowledgement from server client is trying to connect to

## Byte Oriented

- Send can write bytes into a TCP connection
- Receiver reads bytes out of it

## Header

- [[Port Numbers\|Port Numbers]]
	- Source and Destination
- SequenceNum
- Acknowledgement number

# Socket

- SOCK_STREAM

