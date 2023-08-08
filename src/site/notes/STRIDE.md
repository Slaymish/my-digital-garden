---
{"dg-publish":true,"permalink":"/stride/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# STRIDE

## Think like an Attacker

- Is risky because
	- Don't know what *they* know or do
	- If you get that wrong, your [[Threat Model\|Threat Model]] will go astray

- Don't start with attackers (when modelling threats)

## Focus On What You're Building

- Follow **Engineering Approach**
	- Predictable
	- Reliable
	- Scalable to a large product
- Can't be dependent on one person
- Ideally, you understand it
- Concrete and testable


***

# How to Threat Model

1. What are you building
2. What can go wrong
3. What are your going to do about it
4. Check your work on 1-3

## What Are You Building

Create a **Model** of the software/technology you're building.

- Abstracts away details so you can look at the whole
- Could make a diagram using [[UML\|UML]]

### Modelling Methods

- Whiteboard diagrams
- Brainstorming
- Diagrams
	- [[Data flow diagrams\|Data flow diagrams]]
	- [[Swim lanes\|Swim lanes]]
	- [[UML State Diagrams\|UML State Diagrams]]
- Mathematical representations of code

## What Can Go Wrong?

- STRIDE mnemonic
	- **S**poofing
	- **T**ampering
	- **R**epudiation
	- **I**nformation Disclosure
		- Permissions
		- Security
		- Network
		- Misc
	- **D**enial of Service
	- **E**levation of Privilege

Structure helps with *completeness* and *predictability*

| Type                   | Description                                                                                                                    | Security Control |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ---------------- |
| Spoofing               | Aimed at accessing and use of another users creds, such as username as password                                                | Authentication   |
| Tampering              | Maliciously change or modify persistent data, eg record in data base, and alteration of data in transit between two computer   | Integrity        |
| Repudiation            | Aimed at performing prohibited operations in a system that lacks the ability to trace operations                               | Non-Repudiation  |
| Information Disclosure | Intending to read a file that one wasn't granted access to                                                                     | Confidentidality |
| Denial of Service      | Attempting to deny access to valid users                                                                                       | Availability     |
| Elevation of privilege | Intending to gain privileged access to resources in order to gain unauthorized access to information or to compromise a system | Authorizaiton    |

***

# Using STRIDE

- Consider how each STRIDE threat would impact your system
	- "How could a clever attacker spoof this part of the system?... tamper with?..."
	- Go through all the letters
	- Use [[STRIDE Tables\|STRIDE Tables]]
- Track issues as you find 
	- Use [[Threat Tracking Tables\|Threat Tracking Tables]]


***

# STRIDE per Element

- Best for beginners

| DFD element | S   | T   | R   | I   | D   | E   |
| ----------- | --- | --- | --- | --- | --- | --- |
| Entity      |     |     |     |     |     |     |
| Data flow   |     |     |     |     |     |     |
| Data store  |     |     |     |     |     |     |
| Process     |     |     |     |     |     |     |

***

