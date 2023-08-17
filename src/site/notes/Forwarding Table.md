---
{"dg-publish":true,"permalink":"/forwarding-table/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-07-2023
***

| Host | Port |
| ---- | ---- |
| A    | 1    |
| B    | 1    |
| C    | 2    |
| D    | 2    |

- Data coming *into* network first goes to modem
- Then *forwards* data to host based on forwarding table

It matches the [[longest matching prefix\|longest matching prefix]] in the table (if there's multiple entries)

Port here is a **physical port**, and the router is telling the *switch* which way to route it, depending on the destination IP.

Once it get correct port on the switch, the switch sends the frame to the correct [[MAC Addresses\|MAC Addresses]]
If it doesn't have a switch (doesn't have multiple ports), the router generally sends to the correct [[MAC Addresses\|MAC Addresses]]
