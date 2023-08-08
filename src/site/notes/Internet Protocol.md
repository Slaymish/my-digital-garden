---
{"dg-publish":true,"permalink":"/internet-protocol/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-07-2023
***

# IP

Used in [[Routing\|Routing]]

- Works **on top** of layer 1/2
- So can connect networks of different technologies

## Global Addressing

- Should be globally unique
- Shouldn't be *flat* (like [[MAC Addresses\|MAC Addresses]])
	- Doesn't have any information of *how* to get to said address

### IP Addresses Are *hierarchical* They Have:

- Network part
	- Identifies the network the host is attached to
	- All hosts on that network share the same network part in their IP address
- Host part
	- Identifies each host uniquely on that specific network

### Classful System

- Divided into 3 classes
- A,B,C

## Service Model

### Unreliable

- IP's service model is **best effort**
	- Packets may get lost/corrupted
	- But it'll try!!
- Benefit of this is it's simplicity

### IP Header Contents

- Version (4 bits) 
	- IPv4
 - Header length (HLen) (4 bits)
 - Type of Service (8 bits)
	 - Different qualities of service
- Length (15 bits)
	- Header length is **variable**
- Ident 
	- used when a router has to **fragment** a packet due to the network tech having a smaller **MTU**
	- Each broken up packet will have the same Ident value
- [[Checksum\|Checksum]] 
{ #b7966a}

	- just on the header, not the data
- A DestinationAddr (32 bits)
- SourceAddr (32 bits)
	- Needed in case they want a response
- The higher layer [[Protocol\|Protocol]] of the packet
	- Needs to know how to interpret the data
- a Time-to-Live (TTL) - Hop-limit (4 bits)
	- Stops packets from ending up in a loop for too long
	- If a router is misconfigured

## Classful IP Allocation

- ICANN
	- Internet Corporation for Assigned Names and Numbers

| Class   | Starting bits | Network Bits | Host Bits | No. Devices |
| ------- | ------------- | ------------ | --------- | ----------- |
| Class A | 0             | 7            | 24        | 16 Million  |
| Class B | 10            | 14           | 16        | 65,000      |
| Class C | 110           | 21           | 8         | 256-2       |

- Issue is that not network bits available
- To address this, introduced [[CIDR\|CIDR]]

***

## Fragmentation and Reassembly

Allow the packets to be **fragmented** (broken up) when they are too big for a given network technology

### Maximum Transmission Unit (MTU)

The largest IP datagram that a network type can carry in a frame

### Path MTU Discovery

- finds the smallest MTU along the path the packets will travel
- Then doesn't let it go that way to prevent fragmentation


