---
{"dg-publish":true,"permalink":"/boyer-moore/"}
---

Related: #programming #java 
Contents: [[COMP261/COMP MOC\|COMP MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/COMP261_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 28-05-2023
***

# Boyer-Moore Algorithm

[[String Search\|String Search]] Algorithm

Go **FROM THE RIGHT** within the search string S, upon a mismatch, we skip until either:
- Mismatch becomes a match
- or S moves past the mismatch character

## Good Suffix Rule

*details not examinable*

- Let *t* be the substring matched by the inner loop. On mismatch we skip until either no mismatch between S and *t*, or S moves past *t*

