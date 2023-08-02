---
dg-home: false
dg-publish: true
---
Related: [[NWEN241 MOC]]
Contents: [[NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 27-07-2023
***

# Address Resolution Protocol

## Reason Its Needed

- Have to send to router first
- Need mac of router
- Need a way to translate [[Internet Protocol]] to [[MAC Addresses]]

Each node on network have a **ARP Table**
Each entry has a TTL (~ 15mins)

## How it Makes the Table

- Host wants to send a datagram to a host
- It know on the same network (so same network bits in IP)
- *broadcasts* an ARP query onto network (sends to everyone)
- Each host checks if matches their IP address, responds if does
	- Includes sender IP address in response
- Originator adds response to ARP table