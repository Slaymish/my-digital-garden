---
{"dg-publish":true,"permalink":"/threat-tracking-tables/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Threat Tracking

Useful when trying to [[Threat Model\|Threat Model]]
Can be used with [[STRIDE\|STRIDE]] (and [[STRIDE Tables\|STRIDE Tables]])

| Diagram Element                            | Threat Type     | Threat                            | Bug ID                                    |
| ------------------------------------------ | --------------- | --------------------------------- | ----------------------------------------- |
| Data flow #4, web server to business logic | Tampering       | Add orders without payment checks | 4553 "need integrity controls on channel" |
|                                           | Info Disclosure | Payment instruments sent in clear | 4554 "need crypto"                        |

| Threat Type | Diagram Element                 | Threat                                          | Bug ID                                    |
| ----------- | ------------------------------- | ----------------------------------------------- | ----------------------------------------- |
| Tampering   | Web browser                     | Attacker modifies our javascript order checking | 4556 "Add order-checking logic to server" |
|             | Data flow #2, browser to server | Failure to auth                                 | 4557 "Enforce HTTPS everywhere"           |
