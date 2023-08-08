---
{"dg-publish":true,"permalink":"/local-area-networks/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 21-07-2023
***

# Local Area Networks

## Motivation

### *in class*

getting two ppl to 'OOO' or 'AHH' if they do at same time, acts as a **Collision**
If they jam, they backoff:
1. Saying. head = you win the channel
2. Tails = you backoff/wait

- They can both get head, and **both** wait for 10 secs
	- then they have a *chance of collision again*

## What We've Learnt

A single ethernet can connect max 1024
A point-to-point link connects only two (like the people).
Wireless networks are range limited (by their *radios*)

**Need another way  to interconnect link**

# LAN

- within a *limited geographical area*
- common used in LANS's are ethernet or wi-fi
	- Meaning high data transfer rates and low latency cause everything local

## Switches

- Home switches can have as few as 5 ports support only 10/100 Mbps,
- Enterprise can have 16,24, or 48 ports, with 10/100 Gbps

## Datagrams

- Connectionless switching

- Each packet is forwarded independently of previous packets that might have been sent to the same dest
- Two successive packets from host A to host B follow completely different paths (perhaps because of a change in the forwarding table at some switch in the network).

- Transferring small chunks of info (sorta like packets or frames)

# [[Virtual Circuits\|Virtual Circuits]]

- QoS can be garrenteed better

Three way to handle headers for source routing:
- rotation
- stripping
- pointer

## Switched Ethernet without Loops

- also need to add a timeout to each entry in the forwarding table
- Bridge can learn **the [[Forwarding Table\|Forwarding Table]]** automatically (which host is what port)
- each modem has its own forwarding table

## With Loops

### How?

- Could be multiple admins (each doesn't see entire network)

To stop it being cyclical (the [[Forwarding Table\|Forwarding Table]] looping), you have to use a:

**[[Spanning Trees\|Spanning Trees]] Algorithm:**
- No admin 'centre' = distributed (for spanning tree construction phase)





