---
{"dg-publish":true,"permalink":"/link-state-packet-lsp/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-08-2023
***

# Link-state Packet (LSP)

Used in [[Routing\|Routing]] in the [[OSPF\|OSPF]] algorithm

## Contains

- ID of the node that created the LSP
- List of directly connected neighbours to node, with the cost of the link to each one
- A sequence number
- A TTL for the packet

