---
{"dg-home":false,"dg-publish":true,"permalink":"/nwen-241/nwen-storage-classes/","dgPassFrontmatter":true}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***
- Not similar to java classes

**Variables have lifetime:**
- begins when allocated memory
- ends when memory is de-allocated

**Variables have scope:**
- Parts of program where var is visible

***

## Lifetime
- Static
	- Exists for the entire program execution
- Automatic
	- Exists when the block that contains 
- Dynamic
	- Exists from allocation to de-allocation of memory
	- Have to explicitly do that


## Scope
- Local
	- Visible in current block
- Global
	- Visible in whole compilation unit
	- From declaration to end of file
- External
	- Visible in all complication units




| C Storage class | Declaration       | Default init value | Init freq                   | Stored in         | Scope    | Lifetime  |
| --------------- | ----------------- | ------------------ | --------------------------- | ----------------- | -------- | --------- |
| auto            | Inside block      | Garbage            | Every time block is entered | Memory            | Local    | Automatic |
| static          | Inside block      | 0                  | Once at program start       | Memory            | Local    | Static    |
|                 | Outside any block |                    |                             |                   | Global   |           |
| Extern          | Outside any block | 0                  | Once at program start       | Memory            | External | Static    |
| register        | Inside block      | Garbage            | Every time block is entered | Maybe in register | Local    | Automatic          |
