---
{"dg-publish":true,"permalink":"/exponential-backoff/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 17-07-2023
***

# Exponential Backoff

Used in [[Access Mediation\|Access Mediation]]
[[Data Link Layer\|Data Link Layer]]


1. Both nodes detect the collision then they both backoff.
2. Then, immediately after, or after x delay, retry.
3. After each try, if it collides again, increases the num of delay number options.
4. Get makes the range of options bigger, until no collision.