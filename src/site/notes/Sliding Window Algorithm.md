---
{"dg-publish":true,"permalink":"/sliding-window-algorithm/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 15-08-2023
***

# Sliding Window Algorithm

Used in [[TCP (transmission control protocol)\|TCP (transmission control protocol)]]

![Pasted image 20230815121658.png](/img/user/Pasted%20image%2020230815121658.png)

Sender keep track of:
- **Last Acknowledgement received** (LAR)
- **Last frame sent** (LFS)

Sender can send up to the sliding window size num of packets
- Allows for multiple frames sent, even if no ack received 

> [!INFO]
> Receiver only ACK's when they've received everything up to and including that packet

- Then sender can slide up to where the receiver ACKed to 
