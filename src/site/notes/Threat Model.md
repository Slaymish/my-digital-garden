---
{"dg-publish":true,"permalink":"/threat-model/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Threat Modeling

Book: Threat Modeling: Designing for Security
- by Adam Shostack
- February 2014

[[Threat Modelling with STRIDE\|Threat Modelling with STRIDE]]

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

A fun way to do it is with [[Security Cards\|Security Cards]]

