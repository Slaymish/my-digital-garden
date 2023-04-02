---
{"dg-publish":true,"permalink":"/nwen-valgrind/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

[[NWEN241/NWEN Run your code\|NWEN Run your code]]

# Valgrind

- Tool for detecting memory management and threading bugs


Steps to use:
1. Compile with -g
2. Run with valgrind

```
gcc -g buggy.c -o buggy // compile

valgrind --leak-check=yes ./buggy // run
```


