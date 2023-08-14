---
{"dg-publish":true,"permalink":"/privileged-programs/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Privileged Programs

## Need for Privileged Programs

- Passwords contained in a file called ==shadow==


If a ==non-privileged== user (a user that doesn't have write permissions to shadow) wants to change their password, they'd need a program with fine-grained access control

## Two-Tier Approach

- Implementing **fine-grained** access makes OS over complicated
	- Where user can change *parts* of a file


Privileged programs are *extensions* for the OS to enforce **fine-grained access control**

### **Daemons:**

- Program that runs in the background
- Needds to run as root or other privileged user

### Set-UID Programs:

Allows user to run a program with the program owners privileges

- Widely used in UNIX
- Marked with a special bit

**Example:**
- The `passwd` program

```
$ ls - l /usr/bin/passwd
```

Every process has **two** user ID:
- Real UID (RUID): Identifies the ==real owner== of a process
- Effective UID (EUID): Identifies ==privilege== of a process

For a normal program, the RUID == EUID




- Why 4755 in `sudo chmod 4755 mycat`





