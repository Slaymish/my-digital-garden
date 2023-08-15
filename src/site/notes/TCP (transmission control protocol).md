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

- Protocol for [[End-to-End Communication\|End-to-End Communication]] layer (layer 4)
- Requires acknowledgement from server client is trying to connect to

> [!INFO]
> TCP is **Byte Orientated**

## Features

- **Reliable Connection**
- Ordered packets
- Dataflow control
- Send can write **bytes** into a TCP connection
- Receiver reads bytes out of it

### Three-way Handshake

1. Client send first message

```
SrcPort = 4500
DstPort = 80

Sequence num = X

Flags = SYN
```

2. Replies

```
SrcPort = 80
DstPort = 4500

Sequence num = Y
ACK num = X + 1

Flags = SYN + ACK
```

3. Client Replies

```
SYN + ACK
SrcPort = 80
DstPort = 4500

ACK num = Y + 1

Flags = ACK
```

## How Its Reliable

- Uses [[Stop and Wait\|Stop and Wait]]
- Send ACKs when for each packet received
- If don't receive ACK before **timeout** ends, resend packet
- Responsibility is on *sender*


This means its slower than optimal.
Because have to wait the RTT before can send another frame.
To help, we have the [[Sliding Window Algorithm\|Sliding Window Algorithm]]

## Sequence Number

- Sequence num of starting *byte*

```python 
starting at 0
	Length of data = 100 bytes
Next sequence num = 100
```

## Flags

1. SYN
2. ACK
3. SYN+ACK

- If ACK bit is 1, receiver knows to pay attention to ACK number

# Header

- [[Port Numbers\|Port Numbers]]
	- Source and Destination
- SequenceNum
- Acknowledgement number

# Socket

- SOCK_STREAM

