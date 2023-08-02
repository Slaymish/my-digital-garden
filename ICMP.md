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

# Internet Control Message Protocol

Defines a collection of error msgs. A *companion protocol* to [[Internet Protocol]]

They are sent back to the *source host* whenever a router/host is unable to process an IP Datagram.

## Example

- Dest host is unreachable
- TTL expired
- [[Internet Protocol#^b7966a\|IP Header checksum]] header checksum failed 
- Reassembly process failed

## Ping

- Sends out a small packet called an *ICMP Echo Request* packet
- Dest automatically responds with an *ICMP Echo Reply* packet
- Source calculates round-trip time (RTT)
	- endTime-startTime

```
PING 130.195.5.5 (130.195.5.5): 56 data bytes
64 bytes from 130.195.5.5: icmp_seq=0 ttl=251 time=42.207 ms
64 bytes from 130.195.5.5: icmp_seq=1 ttl=251 time=8.362 ms

2 packets transmitted, 2 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 8.362/25.285/42.207/16.922 ms
```

## Traceroute

- Your computer sends packets with a TTL of 1 (only one hop)
- Router that receives will return a *ICMP Time Exceeded* back
- This means our computer will know the first hop in the route
- Will continue, increasing the TTL by one each time
	- Until the entire route is resolved

```
traceroute to 130.195.5.5 (130.195.5.5), 64 hops max, 52 byte packets
 1  10.140.0.2 (10.140.0.2)  18.232 ms  4.249 ms  5.024 ms
 2  10.248.255.7 (10.248.255.7)  10.939 ms  8.065 ms  6.742 ms
 3  10.9.1.66 (10.9.1.66)  6.597 ms  8.303 ms  8.778 ms
 4  130.195.199.194 (130.195.199.194)  8.793 ms  6.569 ms  6.038 ms
 5  ecs.wgtn.ac.nz (130.195.5.5)  5.727 ms  4.948 ms  5.971 ms
```