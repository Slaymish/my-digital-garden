---
{"dg-publish":true,"permalink":"/dhcp/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-07-2023
***

# Dynamic Host Configuration Protocol

- Used to assigned [[Internet Protocol\|Internet Protocol]] addresses
- Network address provided by ISP
- Need to be assigned to *host* part

## How it Happens

*Everyone of network can see this*

1. Client broadcasts *DHCP discover*
2. DHCP server broadcasts back *DHCP offer* (an IP you can use)
3. Client broadcasts *DHCP request*
4. Server broadcasts *DHCP ACK*

## What DHCP Can Broadcast

On top of allocating IP

- IP of first-hop router
- DNS server address

