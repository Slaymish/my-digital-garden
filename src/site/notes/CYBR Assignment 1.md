---
{"dg-publish":true,"permalink":"/cybr-assignment-1/"}
---

Related: #programming #java 
Contents: [[CYBR271 MOC\|CYBR271 MOC]]
[CYBR Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CYBR271_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Assignment #1

Due Sunday, 13 Aug 2023 , worth 25% of the final grade, automatic late day marked out of 100.


- When identifying threats
	- State how to mitigate
		- And exactly how that'd be implemented
		  - eg: Ask person for token/password. Could also use MFA . System will send txt to person, with access code before allow registration to complete.

[[CYBR Assignment 1 PDFs\|CYBR Assignment 1 PDFs]]

[[CYBR Assignment - The System\|CYBR Assignment - The System]]


![300][SCR-20230731-qgxl.png]


- Here are the instructions on how to complete the assignment [(pdf)](https://ecs.wgtn.ac.nz/foswiki/pub/Courses/CYBR271_2023T2/Assignments/CYBR_271_Assignment_1_2023.pdf).
- Download a set of security cards [(link)](https://securitycards.cs.washington.edu/assets/security-cards-deck.pdf).

- Details of the Aircraft Service Scenario [(pdf)](https://ecs.wgtn.ac.nz/foswiki/pub/Courses/CYBR271_2023T2/Assignments/Aircraft-Service-Scenario-2023.pdf)
- Use this template to complete PART 1 of the assignment [(docx)](https://ecs.wgtn.ac.nz/foswiki/pub/Courses/CYBR271_2023T2/Assignments/CYBR_271_SECURITYCARDS_2023_template.docx) [(pdf)](https://ecs.wgtn.ac.nz/foswiki/pub/Courses/CYBR271_2023T2/Assignments/CYBR_271_SECURITYCARDS_2023_template.pdf)
- Use this template to complete PART 2 of the assignment [(docx)](https://ecs.wgtn.ac.nz/foswiki/pub/Courses/CYBR271_2023T2/Assignments/CYBR_271_STRIDE_2023_template.docx) [(pdf)](https://ecs.wgtn.ac.nz/foswiki/pub/Courses/CYBR271_2023T2/Assignments/CYBR_271_STRIDE_2023_template.pdf)
- When you are done, make sure that you submit **security-cards.pdf** and **stride.pdf** [(link)](https://apps.ecs.vuw.ac.nz/submit/CYBR271/Assignment_1)

# Part 1 - Security Cards

## 1 .Identify Human Impacts

For each [[Security Cards\|card]], answer the questions on the card with respect to a stakeholders.
Stakeholder = "An individual, team, organization, or classes thereof, having an interest in a system"

Keep answer to 1-2 sentences

1. Emotional wellbeing
![160][SCR-20230803-oawh-2.png]

- If there was an attack on the service app, and the public is made aware of it, it may cause a lack of peace of mind or fear of flying because they are unsure if its safe


1. Financial wellbeing
![160][SCR-20230803-obem-2.png]

- Inaccurate maintenance records could lead to costly repairs or aircraft downtime, harming an airline's bottom line.

1. Personal data
![160][SCR-20230803-obiz-2.png]

- A data breach exposing maintenance technicians' personal information like certification credentials could enable identity theft.

1. Physical wellbeing
![160][SCR-20230803-obnl-2.png]

- Improper maintenance procedures recorded in the app may risk lives if issues are missed on an aircraft.

4. Relationships
![160][SCR-20230803-obrc-2.png]

- Unauthorised access to an airline's maintenance data could erode competitive advantage and relationships with suppliers.

7. Societal Wellbeing
![160][SCR-20230803-obvh-2.png]

- Systematic falsification of maintenance records enabled by the app could undermine public trust in aviation safety standards.

1. The BioSphere
![160][SCR-20230803-ocaj-2.png]

- Flaws in the service app allowing unsafe aircraft to fly could lead to crashes harming the surrounding environment.

## 2. Identify Threats to the System

**Threat 1:** !!!

- **Threat**: Malicious insider steals and sells confidential maintenance records.
- **Motivation** (Financial Gain): An insider could sell an airline's proprietary data for profit. As a trusted employee they already have access.
- **Resources** (Authority): The insider's authorised access to maintenance records provides the opportunity to steal data. Their job role enables the attack.
- **Method** (Theft): The adversary directly exfiltrates confidential data they have access to and sells it to competitors for financial gain.

**Threat 2:** !!

- **Threat** Competitor attacks the service database and falsifies maintenance records and removes required services 
- **Motivation** (Money): To sabotage their competitors planes, hoping to ruin that companies reputation
- **Resources** (Money): Due to the size of airlines, the malicious competitor could bribe workers for access to the system. They have the funds to allow this.
- **Method** (Manipulation or Coercion): The adversary bribes certified workers to delete important service documents or for access to do it themselves

**Threat 2:** !

- Threat: Hactivist defaces public website to cause PR damage.
- Motivation (Ideological Belief): A hactivist seeks to further their ideology by damaging an airline's image.
- Resources (Computer Skills): The hactivist has the technical skills to exploit a vulnerability in the public website.
- Method (Defacement): By hacking the website and replacing content, the hactivist aims to embarrass the airline publicly.

**Threat 3:** !!

- Threat: Skilled attacker modifies maintenance records to hide deficiencies.
- **Motivation** (Ego): Hacker wants to prove they can breach the system for bragging rights.
- **Resources** (Computer Skills): Attacker has the technical expertise to exploit app vulnerabilities.
- **Method** (Tampering): By modifying maintenance logs, the hacker can undermine safety without detection.
- Human Impact: This threatens public safety by hiding aircraft maintenance issues.

**Threat 4:** !!

- Threat: Criminals clone stolen tablets to gain maintenance access.
- **Motivation** (Financial Gain): Seek to enable smuggling by controlling app access.
- **Resources** (Physical Proximity): Ability to physically access tablets to copy data.
- **Method** (Spoofing): Cloned tablets allow unauthorised access to app functions.
- Human Impact: Could enable smuggling and circumvent customs processes.

**Threat 5:** !!

- Threat: Faulty app update deletes maintenance records.
- **Motivation** (Career Advancement): Developer wants to release changes quickly.
- **Resources** (Authority): Access to update the application code.
- **Method** (Destruction): Bugs introduced corrupt/delete data.
- Human Impact: Aircraft risk operating without maintenance history.

**Threat 6:** !

- Threat: Unencrypted connections expose airline's data.
- **Motivation** (Ideological Belief): Hactivist wants to damage image.
- **Resources** (Computer Skills): Ability to intercept WiFi communications.
- **Method** (Interception): Plaintext data on public networks is captured.
- Human Impact: Undermines airline's competitive advantage.

**Threat 7:** !!

- Threat: Disgruntled employee wipes maintenance databases.
- **Motivation** (Revenge): Wants payback for perceived mistreatment.
- **Resources** (Authority): Access privileges to delete data.
- **Method** (Destruction): Deletes records to cause business disruption.
- Human Impact: Costly aircraft downtime and delays (money?)

## 3. Identify the Most Relevant Threats

By relevant, I mean the threats I perceive as the most likely to happen in the context of the given scenario, as well as possible impact of the threat happening.

### Threat 1

- Malicious insider steals and sells confidential maintenance records.
	- This is relevant because of how realistic is it. There's currently no safe guards to prevent this, and many of the competitors would like this information and may be willing to pay

### Threat 2

- Competitor airline attacks the service database and falsifies maintenance records and removes required services
	- I think this is relevant because profit motivated companies have done espionage before, and it would monetarily benefit them.
	- Also I think the impact of this could be severe as unserviced planes may be flown, which could lead to crashes/physical harm on their customers

### Threat 3

- Disgruntled employee wipes maintenance databases.
	- I think this is relevant because it would cause a large monetary loss to the company as they would have to delay and possible recheck all planes, as they would have lost all information on them

## 4. Propose how to Mitigate the Threats

### Mitigation 1

- Malicious insider steals and sells confidential maintenance records.
	- Limit the amount each employee has access to to a minimum.
	- Only let them view the maintenance records they need to see at the present moment
	- Log (and flag) when employees try to access records that they are not currently assigned to. This could allow for early detection of the threat, and may give the company enough time to stop the employee before they sell the records

### Mitigation 2

- Competitor airline attacks the service database and falsifies maintenance records and removes required services
	- Require multiple certified people to signoff services instead of just one.
	- This would limit the amount of harm one person could do.
	- This may be inconvenient and lead to more admin work for the employees

### Mitigation 3

- Disgruntled employee wipes maintenance databases.
	- Store multiple online and offline backups of the entire maintence database, and regularly sync to keep them updated.
	- This would mean even if it were wiped, you'd be able to restore from a backup
	- This will cost more money to have extra backup servers/storage


***

# Part 2 - STRIDE

## Assume the following

#### first thoughts:

- HTTP for web app, allows for sniffing/injection
- Legacy web app, cookie could get stolen/stored. Anyone with cookie would be able to be logged in
- Could intercept traffic beign sent frm API server to Tablets
	- Could store to steal/sell
	- Alter data before tablets receive it
- Same google id
	- means disgruntled employee will still have it
- Games/apps installed on tablets
	- Malicious app install (intentionally or otherwise)
- 