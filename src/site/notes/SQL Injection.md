---
{"dg-publish":true,"permalink":"/sql-injection/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# SQL Injection

On the [[OWASP Project\|OWASP Project]] top ten

## Vulnerable when

- User data is not sanitized



**Example Attack**

```
query = "SELECT \* FROM accounts WHERE custID='request.getParameter('id')'
```