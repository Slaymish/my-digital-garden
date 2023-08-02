Related: #programming 
Contents: [[NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 27-02-2023
***

- You can not
	- Change the size after init
	- Assign a new array using '='

- Arrays automatically 'decay' into pointers
	- Loses info about size


***

# Pointers and Arrays

^822933

- Arrays are a fixed [[NWEN Pointers\|pointer]] to the first array element
	- Therefore cannot reassign an array

**Example**

```C
int z[10] = {1, 2, 3};
```

- z is a fixed pointer, it points to the address of z[0]
- z == &z[0]



