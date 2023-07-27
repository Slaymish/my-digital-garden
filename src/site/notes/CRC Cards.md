---
{"dg-publish":true,"permalink":"/crc-cards/"}
---

Related: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
Contents: [[SWEN225 MOC\|SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 24-07-2023
***


Object orientated construction (2nd edition)

# CRC Cards

- Classes
- Responsibilities 
- Collaborators

## Responsibilities

- High level (not single operations)
- what to know and what to do
- short phrases containing an **action verb**

## Collaborators

- Other classes that are needed to perform a task or to get information from

| Board                |          |
| -------------------- | -------- |
| aggregates locations | Location |
| knows item locations | Item     |
| observes game status | Storage  |

## For Sokoban

- We have a *list of responsibilities*
- need to associate each responsibility to a class

```
- managibng locations
- knowing locations of items
- knowing if a storage location is full
- deciding when game is over
- knowing which directions the worker can move towards
- knowing whether the worker moves, pushes, or places
- etc.,..
```

| Board                |          |
| -------------------- | -------- |
| aggregates locations | Location |
| knows item locations | Item     |
| Knows game status    | Storage  |

| Worker         |           |
| -------------- | --------- |
| Knows position | Location  |
| Moves,         | Location, |
| pushes,        | Crate     |
| places         | Storage   |

- By having the location be the Location classes responsibility (not worker), allows for method of location to not be set in stone

| Location         |            |
| ---------------- | ---------- |
| Knows position   | Coordinate |
| Knows neighbours |            |

| Storage        |     |
| -------------- | --- |
| Knows location | Location    |
