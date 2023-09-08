---
{"dg-publish":true,"permalink":"/buffer-overflow-counter-measures/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Countermeasures

## Developer Approaches

1. Check data length
2. Don't let users set the length, set it yourself (`strncpy` instead of `strcpy`)

```
char *strncpy(char *dest, const char *src, size_t n)
```

3. Use a safer library (libsafe)
	1. Knows where ebp is and stops if about to overwrite it
4. Use safer languages

## OS Approaches

- ASLR
- Shell program defences
- Non-executable stack

## Compiler Approaches

- Stack-Guard