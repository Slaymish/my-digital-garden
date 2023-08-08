---
{"dg-publish":true,"permalink":"/uml-class-diagram/"}
---

Related: [[SWEN221/SWEN221 MOC\|SWEN221 MOC]]
Contents: [[SWEN225 MOC\|SWEN225 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/SWEN225_2023T2/CourseSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 12-07-2023
***

# Classes in UML

Classes have **three** sections:
- Top == name of call
- Middle == **Attributes**
- Bottom == methods

## Attributes

- aka fields,variables,properties

**Formatting**

```
-name: string
-id: int
-age: int
```

## Methods

**Formatting**

```
-setName()
+eat()
```

# Visibility

- *Exact* meaning is a [[semantic variation point\|semantic variation point]]

| Symbol | Description |
| ------ | ----------- |
| -      | Private     |
| +      | public      |
| #      | protected   |
| ~      | package/default|

# Relationships

**Inheritance**
- Arrow goes **into** parent class, from subclass
- Association
	- No arrow, connection between classes

**Aggregation** - Hollow Diamond

 - Airplanes in an airport
	 - Have a collections of things that can exist on their own
- No additional semantics
- If in doubt, use reg association (just a line)


**Composition** - Black Diamond
 - An engine in a car
	  - The contained item is a part of the containing item
- Synchronises lifetimes (transitively)
- Anti-symmetric

## Associations

- Association have names
	- That describe the relationship
- Associations have role names

Eg:
- produces, enables etc

| Cetegory            | Example                   |     |
| ------------------- | ------------------------- | --- |
| A is a member of B  | Pilot-Airline             |     |
| A uses or manages B | CEO-Airline               |     |
| A communicates to B | Pilot-Air traffic control |     |

# Multiplicities

Goes next to class, specifies how many instances can be made of a class

- Implicitly is one

- `1` =  exactly one
- `1..*` = one or more
- `*` = many (zero or more)
- `0..1` = optional (zero or one)
- `2..4,6..8` = Numerically specified

## Extends/Implements

- Extends == solid line
- Implements == dashed line