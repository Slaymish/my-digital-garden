---
{"dg-publish":true,"permalink":"/nwen-243-test-prep/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-08-2023
***

# Mid-Term Test

Procedural:
- ip forwarding
- lookup table

## IP Addresses

- See [[Internet Protocol\|Internet Protocol]]

## Routing Tables

- [[Routing\|Routing]]
- [[Forwarding Table\|Forwarding Table]]
- [[NWEN243 Project 1#Q5\|NWEN243 Project 1#Q5]]

# Questions

1. True
2. false, its affect by distance, the transport medium and signal speed [[Propagation Delay (Link Latency)\|Propagation Delay (Link Latency)]]
3. False, its used for collision avoidance (congestion control)
4. False, quadrubling,  IPv4 is 32bits
5. Flase, [[ICMP\|ICMP]] is used for error handling and diagnostics like [[Ping\|Ping]] and [[TraceRoute\|TraceRoute]]
6. False its the [[Sliding Window Algorithm\|Sliding Window Algorithm]] is used for flow control
7. False, [[Local Area Networks\|Local Area Networks]] has to be in same geographical area, not same physical location
8. True
9. False, [[fragmentation\|fragmentation]] is usually avoided as much as possible
10. False, it for identifying devices on a [[Local Area Networks\|Local Area Networks]] (sharing the same link)
11. true, [[OSPF\|OSPF]] does use [[Djikstra's Algorithm\|Djikstra's Algorithm]]
12. [[CSMA\|CSMA]] true
13. [[Stop and Wait\|Stop and Wait]] false, it **sends one segment at a time and wait for acknowledgement**
14. [[ARP\|ARP]] true
15. False, each packets path is decided independently

## More Questions!!

1. [[Data Link Layer\|Data Link Layer]] false, it converts data to bits so it can be carried on the transmission medium
2. True
3. [[IaaS\|IaaS]] true
4. [[ICMP\|ICMP]] true
5. [[CSMA\|CSMA]]/CD, false this protocol is used to detect collisions (**Used in ethernet**)
6. [[Sliding Window Algorithm\|Sliding Window Algorithm]] true
7. [[OSPF\|OSPF]] true - **link-state routing protocol**
8. False, [[fragmentation\|fragmentation]] decreases the efficiency of a network
9. [[DHCP\|DHCP]] false, it is used to dynamically assign [[Internet Protocol\|Internet Protocol]] addresses
10. true [[MAC Addresses\|MAC Addresses]], **false, purpose is distinction between devices sharing the same link**
11. False, each packet gets forwarded independently
12. False, the first 24bits are used for the network portion
13. [[Propagation Delay (Link Latency)\|Propagation Delay (Link Latency)]], false it also depends on speed on signal, transmission medium
14. [[Exponential backoff\|Exponential backoff]], false its used to avoid collisions
15. [[SaaS\|SaaS]] true

## More Questions!!!!!

1. To transfer HyperText between a client and a server
2. Applications can all use the same protocol, just implement it differently (eg web browsers)
3. SSH
4. Persistent TCP connection between requests
5. PUT will only place one entry for something, while POST will create a new one every time
6. To dynamically assign devices on a network an IP address
7. the startline has the request type, the url, and http version
8. THE CRLF specifies a new line
9. idempotent means it won't create duplicate copies if somethings sent multiple times (ie PUT is idempotent while POST is not)
10. SNMP manages network devices (Service protocol)
11. WebSocket protocol **allows for real-time, two-way communication**
12. Non-linear means you can traverse through different documents in any order
13. <https://accounts.example.com/place?user=hamish&pass=myPass>

```
https = protocol
accounts = subdomain
example.com = domain name
/place = path
? = query
user=hamish&pass=myPass = params
```

14. HTTP isn't aware of any past information. If you want states, pass the state information in the message body (ie as cookies)
15. [[SMTP\|SMTP]] and [[IMAP\|IMAP]]

## More... Questions!!......

1. Framing is used to define boundaries between frames
2. [[Propagation Delay (Link Latency)\|Propagation Delay (Link Latency)]]. Influences by signal strength, transmission medium, and distance between nodes
3. IPv6 is 128bits, and displayed in hex. IPv4 is 32bits and displayed in decimal.
4. [[ICMP\|ICMP]], traceroute traces the path packets take through the network 
5. [[ARP\|ARP]] to translates IP addresses into [[MAC Addresses\|MAC Addresses]]
6. [[Exponential backoff\|Exponential backoff]] is used in the [[Data Link Layer\|Data Link Layer]] to enable [[Collision Avoidance\|Collision Avoidance]]. It does this by timing out at random intervals anytime it detects a carrier. This decreases the likelihood that two packets will be sent at the same time
7. [[CIDR\|CIDR]] notation denotes the network bits (from the start)
8. [[Sliding Window Algorithm\|Sliding Window Algorithm]] - Allows the sender to send multiple frames
9. [[OSPF\|OSPF]] link-state routing - An LSP floods a network, in order to update routing tables with the best possible routes
10. HTTP GET **requests** while POST **responds**. POST is also idemotic
11. [[CSMA\|CSMA]] - CSMA is a protocol that any time a carrier is sensed, it won't transmit anything until it can no longer sense it. It then will send the **entire packet**
12. [[Client-Server Paradigm\|Client-Server Paradigm]] - [[Application Layer Protocols\|Application Layer Protocols]] - Protocols like HTTP follow the [[Client-Server Paradigm\|Client-Server Paradigm]]. This means that one of the nodes is a server (always on, static perm ip), and the other is a client (only usually connects with server, Dynamic ip).
13. [[Stop and Wait\|Stop and Wait]] - responsibility on sender. If don't receive acknowledgement for a sent packet, wait for timeout to end then resend it.
14. [[ICMP\|ICMP]] [[TraceRoute\|TraceRoute]] works by sending a series of packets to a node, starting with a TTL of 1 and incrementing it for each packet. When the TTL reaches zero, the node its at sends back a [[ICMP\|ICMP]] time exceeded packet to the source IP. This lets the person doing the trace-route see each node allow the packets path.
15. [[DHCP\|DHCP]] Dynamic allocation of IP addresses