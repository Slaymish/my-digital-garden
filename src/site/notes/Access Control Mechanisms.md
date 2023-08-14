---
{"dg-publish":true,"permalink":"/access-control-mechanisms/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Access Control Mechanisms

## Discretionary Access Control (DAC)

This is what happens in Windows, Linux, Mac, Unix

- ==Owner== of object specifies who can access object (files/directories)
- Control access on discretion of owner
- **Access Privileges decided when file created**

### Filesystem Access Control

- [[Access control lists\|Access control lists]] (ACLs)
- [[Role-Based Access\|Role-Based Access]] (RBAC)

#### Unix File Permission

- `ls -l`

| Directory/file/link | User rights | Groups rights | Others rights |
| ------------------- | ----------- | ------------- | ------------- |
| `-`                 | `r w x`     | `r w x`       | `r w x`       | 

### Unix Users and Root

- Special user **root** and can do ==anything== on the system
	- Aka superuser (sudo)
- Unix identifies user using a UID
- Users can be granted rights/permissions

## Mandatory Access Control (DAC)

Secret, confidential
Happens in **SELinux**

- ==System== decides which **subjects** (users/processes) can access which objects
- Subject are given clearance
- Objects are given security classification