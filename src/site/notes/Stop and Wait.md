---
{"dg-publish":true,"permalink":"/stop-and-wait/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-08-2023
***

# Stop-and-wait

Used in [[TCP (transmission control protocol)\|TCP (transmission control protocol)]]

- Send ACKs when for each packet received
- If don't receive ACK before **timeout** ends, resend packet
- Responsibility is on *sender*
