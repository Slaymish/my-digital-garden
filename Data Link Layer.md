---
dg-home: false
dg-publish: true
---
Related: [[NWEN241 MOC]]
Contents: [[NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 13-07-2023
***

# Physical Layer Abstraction

The physical layer (layer 1) encodes bits onto the transmission medium so it can be understood by a receiving node. This is abstracted away, so you only really have to think of the Operation properties.

Operation properties summarised as:
- [[Throughput]]
- [[Bit-error rate]]
- [[Propagation Delay (Link Latency)]]


Even with a physical *layer*, we have some issues we need to solve

# Need for a Data Link Layer (Layer 2)

[[Framing]]: How does the receiving node know where a chunk of msgs start/end? 
[[Error Detection]]: How can the *receiving node* know if they encountered any errors? 

# Headers and Trailers

![200][SCR-20230713-mkut-2.png]

# Access Mediation

- Multiple node may share the same link
- They could all be connected to a repeater, which is a **Physical Layer** device (just deals with signals and stuff)
- Need a way to differentiate between diff data send/received on network 

- [[CSMA]] Carrier Sensing Multiple Access

## Collision Detection

- Can't be completely avoided with CSMA

### If You Detect a Collision

Both nodes detect the collision then they both backoff.
Then, immediately after, or after x delay, retry.
After each try, if it collides again, increases the num of delay number options.
Get makes the range of options bigger, until no collision.
This is what [[Exponential backoff]] is.

## Channel Partitioning

- Different devices will want to share their own data, so we must split them up into different channels

- **TDMA** (Time division multiple access)
	- only allowed to send/receive your stuff in your allocated time slot
	- So no overlap
	- Can be wasteful if a device has been allocated some time and doesn't use it
- **FDMA** (Frequency division multiple access)
	- Have each channel broadcasted at different frequencies
- **CDMA**, **OFDMA** etc
	- Combination of above two


All the above require a **centralised coordinator** to assign time/freq to each new device
Goal is to have a *decentralised* system, that doesn't rely on synchronisation of clocks etc

## MAC Address

- To distinguish the nodes from each other
- Should be unique
- The source and dest addresses go in the [[Data Link Layer#Headers and Trailers\|Header]]

## RTS-CTS

- To avoid collisions between multiple nodes
- Requires adknowledgement for everything
- Recapped next lect