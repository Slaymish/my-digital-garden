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

# STIDE Tables

Use STRIDE tables to write your analysis and ideas

| Threat              | What the attacker does                   | Notes/Examples                                                     |
| ------------------- | ---------------------------------------- | ------------------------------------------------------------------ |
| Spoofing a process  | Create a file before the real process    | Then your process relies on it                                     |
|                    | Abuses names                             | Creates a version of 'sudo' and alter PATH                         |
| Spoofing a filename | Create a file in the local directory     | Library executable or config file                                  |
|                    | Creates a link, changes it               | Also called 'race condition' or TOCTOU (time of check/time of use) |
|                     | Creates many files in a target directory | Code can easily create all possible /tmp/foo.random                                                                   |

## Spoofing over a Network

| Threat Example     | What the attacker does              | Notes                                     |
| ------------------ | ----------------------------------- | ----------------------------------------- |
| Spoofing a machine | [[ARP spoofing]]                        |                                           |
|                    | IP Spoofing                         |                                           |
|                    | [[DNS Spoofing]]                        |                                           |
|                    | [[DNS compromise]]                      | Can be at the TLD, register or DNS server |
| Spoofing a person  | Take over account                   | "Stranded in london"                      |
|                    | Set the display name                |                                           |
| Spoofing a role    | Declares themselves to be that role | Sometimes opening a special account, setting up a domain/website, other 'verifiers' |

## Tampering with a File

| Threat Example                  | What the attacker does         | Notes |
| ------------------------------- | ------------------------------ | ----- |
| Modifying a file                | ..which you own and rely on    | ...   |
|                                 | which they own and you rely on |       |
| Modifying a file on a server... | ...you own                     |       |
|                                 | ...they own (or take over)     |       |
| Modifies links or redirects     |                                | Redirects are super common on web      |

## Tampering with Memory

| Threat Example                  | What the attacker does                                      | Notes                                                                          |
| ------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Modifying code                  | change your code to suit themselves                         | hard to defend against if attacker is running code inside **trust boundaries** |
| Modifying data they've supplied | supplies data to a pass by reference API, then changes it   | Works because of TOCTOU issues                                                 |
|                                 | Supplies data into a shared memory segment, then changes it |                                                                                |

## Tampering with a Network

| Threat Example                              | What the attacker does                                   | Notes                                        |
| ------------------------------------------- | -------------------------------------------------------- | -------------------------------------------- |
| Redirects the flow of data to their machine | uses an attack at some network layer to redirect traffic | Pakistan/Youtube Story (wanted to ban it)    |
| Modifies data flowing over the network      |                                                          | Easier (and more fun) with wireless networks |
|                                             | Uses network tampering to improve spoofing attacks       |                                              |

## Repudiation

| Threat Example        | What the attacker does      | Notes                                                                    |
| --------------------- | --------------------------- | ------------------------------------------------------------------------ |
| Repudiating an action | Claims to have not clicked  | Maybe they did, maybe they didn't, maybe they're confused                |
|                       | Claims to not have received | Receipt is strange; does a client downloading email mean you've seen it? |
|                       | Claims to be a fraud victim |                                                                          |
|                       | Uses someone elses account  |                                                                          |

## Repudiation Attacks on Logs

| Threat Example                         | What the attacker does               | Notes          |
| -------------------------------------- | ------------------------------------ | -------------- |
|                                        | Discovers there are no logs          |                |
| Modifies data flowing over the network | Puts data in the logs to confuse you | `</tr></html>` |

## Information Disclosure (Processes)

| Threat Example           | What the attacker does                             | Notes                                                             |
| ------------------------ | -------------------------------------------------- | ----------------------------------------------------------------- |
| Extracts user data       | Exploits bugs like SQL injection to read db tables | Can find this by looking to data store                            |
|                          | Reads error messages                               | Sometimes can contain a bunch of secret info                      |
| Extracts machine secrets | Reads error messages                               | Cannot connect to data 'foo' as user 'sql' with password '&IO*(^' |
|                          | Exploits bugs                                      | "Heartbleed"                                                                  |

## Denial of Service

- Can be temporary (as the attack continues; fill the network) or persist beyond that (fill a disk)

| Threat Example       | What the attacker does                    | Notes                     |
| -------------------- | ----------------------------------------- | ------------------------- |
| Against a process    | Absorb memory (ram or disk)               |                           |
|                      | Absorb CPU                                |                           |
|                      | Against business logic                     | "too many login attempts" |
| Against a data store | Fills the data store                      |                           |
|                      | Makes enough requests to slow down system |                           |
| Against a data flow  | Consumes network resources                |                           |

## Elevation of Privilege ('EoP')

| Threat Example                     | What the attacker does                                | Notes                                                      |
| ---------------------------------- | ----------------------------------------------------- | ---------------------------------------------------------- |
| EoP against process via corruption | Sends inputs the code doesn't handle properly         | Very common, high impact                                   |
|                                    | Gains read/write access to memory   (stack smashing?) | Writing memory more obviously bad                          |
| EoP via misused auth checks        |                                                       |                                                            |
| EoP via buggy auth checks          |                                                       | centralizing checking makes consistency/correctness easier |
| EoP via data tampering             | Modify bits on disk                                                      |                                                            |
