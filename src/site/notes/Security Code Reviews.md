---
{"dg-publish":true,"permalink":"/security-code-reviews/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Security Code Reviews

- Auditing the source code for an application
- To verify that the proper security controls are present, work as intended, and have been invoked in the right places

<https://owasp.org/www-project-code-review-guide/assets/OWASP_Code_Review_Guide_v2.pdf>

## Why?

- Sooner you find the security issue the better
- Cost increases at different stages of Software Development lifecycle

## Source Analysis Tools

**Static automated tools**
- Will basically go through weakness/vulnerability lists
- And tell you if you have any issues

**flawfinder**

- Opensource tool
- C/C++ source code analyser
- Provides [[MITRE Projects#Common Weaknesses Enumeration (CWE)\|MITRE Projects#Common Weaknesses Enumeration (CWE)]]

**Coverity**
- Commercial static code analysis tool
- <https://scan.coverity.com/>

## Variations

**Inspection:**
- A more formalized code review with
	- roles
	- several reviewers looking at same piece of code
	- Specific expected outcomes

**Walkthrough:**
- Informal discussion of code between author and a single reviewer

**Code Reading:**
- Reviewers look at code by themselves
- No actual meeting
- This is what most open source things look like

### Standards

- NIST Cybersecurity framework and publications
- NZ information security Manual (GCSB)
- Payment card industry data security standard (PCI)

## Google Code Reviews

- Every code change is reviewed
- Company-wide approval criteria
- Small reviews completed within one hour
- Large reviews within five hours
- Small and frequent reviews

## Security Testing

- Code never works the first time!
- Must test it to find bugs

See [[SWEN221/Java Testing\|Java Testing]]

It just increases confidence in the software. No guarantee.

Ordinary testing focuses on:
- Happy path
- Unhappy path

For *security bugs*:
- Unhappy paths are failures due to errors made by programmer
- Security bugs are caused deliberately by attacker


**Security Bugs:**
- Focus on less likely to occur failures
- Meeting the attacjers goals
- Highest return on investment (for the attacker)

# Building a Security Test Plan

1. Make a [[Threat Model\|Threat Model]]
2. Use information from the threat model
3. Test the mitigations you added











