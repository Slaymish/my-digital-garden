---
{"dg-publish":true,"permalink":"/9-bit-permission-model/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# 9-bit Permission Model

|     | r   | w   | x   |
| --- | --- | --- | --- |
| u   | 1   | 1   | 1   |
| g   | 1   | 0   | 1   |
| o   | 1   | 0   | 1   |

u = 3
g = 2
o = 2

```
u = File owner Permissions
g = group Permissions
o = other Permissions (ie not pert of both owner or group)
```

Rows add to each number in `chmod` cmd

- Used in `chmod`
- Octal numbers

```
sudo chmod 4755 myProgram
```

- 7 = user
- 5 = groups
- 5 = others 

- 4 is a special attribute

## Permissions

```
r = readable
w= writable
x = executable or directory is searchable
```

### Example

`ls -l /etc`

```
From mac terminal (so may be different) 

lrwxr-xr-x@ 1 root  wheel  11  2 Jun 16:36 /etc -> private/etc
```

Fields are:

- `lrwxr`
- `xr`
- `x@`
- UID = `root`
- GUID = `wheel`

