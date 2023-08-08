---
{"dg-publish":true,"permalink":"/udp/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 07-08-2023
***

# User Datagram Protocol

Out of list in [[End-to-End Communication\|End-to-End Communication]], only does:

- Supporting multiple application processes on each host

## Connectionless

- No handshaking between UDP sender/receiver
- Each UDP segment handled independently of others

Because does not need connection, and has a **small header size**, it can send as fast as desired (with low overhead)
- Eg streaming apps 
- [[DNS\|DNS]]
- Simple network management protocol [[SNMP\|SNMP]]

Can add reliability at **application layer**


## Header

- Contains [[Port Numbers\|Port Numbers]]