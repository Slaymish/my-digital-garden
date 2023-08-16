---
{"dg-publish":true,"permalink":"/end-to-end-communication/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 07-08-2023
***

# End-to-End Communication (Layer 4)

## What You Need it for

- Supporting multiple application processes on each host
- Guarantee of message delivery
- Delivery of messages in the same order they're sent
- Delivery of at most one copy of each message
- Supporting arbitrarily large messages
- Supports synchronisation between the sender and the receiver
- Allowing the receiver apply flow control to the sender
- Security (eg CIA)

First solution: [[UDP\|UDP]]
or [[TCP (transmission control protocol)\|TCP (transmission control protocol)]]

## Mux/Demux

- Each host can run multiple applications
- Need a way to differentiate the messages
- What a [[Port Numbers\|Port Numbers]] is

## Encapsulation/Decapsulation

