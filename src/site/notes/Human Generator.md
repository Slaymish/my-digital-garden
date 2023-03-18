---
{"dg-home":false,"dg-publish":true,"permalink":"/human-generator/","dgPassFrontmatter":true}
---

Related: #
[[UNI MOC\|UNI MOC]]
Hamish Burke || 19-03-2023
***


**purpose: to speedup of workflow of ai prompt gen gig on fiverr. app:**


**App:** *Ask user for prompt requirements*
- Make api call to GTP3.5-turbo
- Have "You are a prompt generator" preamble as a var
	- bulletpointed

**App:**. *Make array of prompts made*
- 2d array (extra slot under each prompt to store img)
- Use scanner, use .UseDelimitor(bulletpoint)

