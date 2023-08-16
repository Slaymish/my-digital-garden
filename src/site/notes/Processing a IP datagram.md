---
{"dg-publish":true,"permalink":"/processing-a-ip-datagram/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-08-2023
***

# Processing of an IP Datagram at a Router

1. IP header validation

2. Process options in [[Internet Protocol#IP Header Contents\|IP header]]

3. Parsing the destination IP address

4. [[Routing\|Routing]] table lookup 

5. Decrement TTL

6. Perform [[fragmentation\|fragmentation]] (if needed) 

7. Calculate [[Checksum\|Checksum]]

8. Transmit to next hop

9. Send [[ICMP\|ICMP]] packet (if needed)