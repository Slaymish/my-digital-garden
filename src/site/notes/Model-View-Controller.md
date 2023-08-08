---
{"dg-publish":true,"permalink":"/model-view-controller/"}
---

Related: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]] [[Design Patterns\|Design Patterns]]
Contents: [[SWEN225 MOC\|SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 02-08-2023
***

# Model-View-Controller

Apparently useful for [[SWEN225 Assignment 2\|SWEN225 Assignment 2]]

**Three-way** division of Application

![300][SCR-20230802-naot-2.png]

representation of data
- Bank accounts

presentation of data
- Balance sheets
- view profile

interacting with data
- button menus direct manipulation

## Advantages

- Separates model and presentation
- Model **does not** depend on GUI used
	- Meaning you can program logic separately
 - Easy to support multiple view

## Example

- User clicks cell (in balance sheet)
- cell **Controller** handles editing
- Controller send Model
- Model updates its field
- Model sends changed to itself
- **View** refreshes itself and queries model for the updated value
	- Could use [[Observer Pattern\|Observer Pattern]] instead for model to notify views
