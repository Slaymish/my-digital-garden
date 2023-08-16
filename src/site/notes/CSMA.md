---
{"dg-publish":true,"permalink":"/csma/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 17-07-2023
***

# Carrier Sensing Multiple Access

Protocol where a node **verifies the absence of other traffic** before transmitting on a shared transmission medium. 

If a carrier is sensed, the node waits for the transmission to end before initiating.
Transmissions by one node are generally received by **all other nodes** connected to the medium.

## CSMA/CA (with [[Collision Avoidance\|Collision Avoidance]])

- Unrealisable because of the [[Hidden Node Problem\|Hidden Node Problem]]
- Operates in **layer 2** (the [[Data Link Layer\|Data Link Layer]])
- Nodes attempt to avoid collisions by beginning transmissions *only* when after the channel is sensed to 'idle'
- When they do transmit, they transmit their packet data in its entirety
- For wireless networks CSMA/CD sometimes not possible, due to wireless transmitters turning off their receivers during packet transmission


If a carrier is sensed, then **transmission is deffered for a random interval**
- This reduces the likelihood that 2+ nodes will simultaneously begin transmission once the channels clear this is **used by Wi-Fi**

## CSMA/CD (with [[Collision Detection\|Collision Detection]])

Used to improve CSMA's performance by **terminating transmission as soon as a collision is detected**

- Used by **Ethernet**




