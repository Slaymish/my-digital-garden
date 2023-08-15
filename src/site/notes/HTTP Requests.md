---
{"dg-publish":true,"permalink":"/http-requests/"}
---

Related: #programming 
Contents: [[CGRA251 MOC\|CGRA251 MOC]]
[CGRA Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CGRA251_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

- Can send HTTP requests, get data while playing
- Could stream in live data

- EG get whether for current loc
- Stream game data from dedicated server
	- AWS instance?
	- Pay to play


- Preferably use open links, not anything requiring auth

```
extends Node

func _ready():
	$HTTPRequest.request_completed(on_request_completed)
	$$
```