---
dg-home: false
dg-publish: true
---
Related: #programming #java 
Contents: [[CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC]]
Hamish Burke || 03-07-2023
***

# Threat Modeling

Book: Threat Modeling: Designing for Security
- by Adam Shostack
- February 2014

[[Threat Modelling with STRIDE]]

## Goal

- Start thinking about threats as early as possible

## Terms

- Asset
	- Something that should be protected
	- Eg money in a bank
- Vulnerability
	- Weakness or lack of protections
	- Unexamined library
- Threat
	- Something that could negatively impact an asset
- Risk
	- The possibility that a threat will exploit a vulnerability to harm an asset
	- Risk = Threat * Vulnerability
 - Security Controls
	 - aka *mitigations*
	 - Protect against threats, reduce vulnerability

## Why

- Non-compliance
- Data-loss

## How

1. Analysing the application/System
2. Determining threats
3. Addressing threats

A fun way to do it is with [[Security Cards]]




***

### For Api's

- Perform security checks inside the boundary
- When using cryptography, make sure its in constant time
	- Can do a [[timing attack]] 

## Mitigate

- Add/use technology to prevent attacks

### Custom Mitigations

- Easy to get wrong
- Hard and expensive to test

***

## Accepting Risk

- Works best when its your risk
- Careful when 'accepting' risk for your customers

### Customer risk Acceptance

- Via UI
	- Eg terms of service
- Sometimes customer has details you can't have 

#### Transferring Risk

- Via lincense agreements, ToS, etc
- Silently
- Both can lead to unhappy customers