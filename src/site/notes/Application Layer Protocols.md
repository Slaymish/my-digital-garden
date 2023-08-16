---
{"dg-publish":true,"permalink":"/application-layer-protocols/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 16-08-2023
***

# Application Layer Protocols

Have to say:
- types of messages exchanged
	- eg request/response
- message syntax
	- whats fields in messages and how they're setup
- message semantics
	- meaning on information in fields

## End User Application Protocols:

- [[HTTP\|HTTP]]
	- Transferring resources on the WWW
- [[SMTP\|SMTP]]
	- Sending outgoing mail
- [[IMAP\|IMAP]]
	- Retrieving emails from a mail server
- [[FTP\|FTP]]
	- Transferring files between client/server
- [[SSH\|SSH]]
	- Providing secure remote access
- [[XMPP\|XMPP]]
	- instant messaging and 'presence'
- [[WebSocket\|WebSocket]]
	- Real-time, two-way communication

## Service Protocols:

- [[DNS\|DNS]]
- [[SNMP\|SNMP]]
	- Managing network devices
- [[SNTP\|SNTP]]
	- Sync time on network devices
- [[DHCP\|DHCP]]
	- Leasing IP addresses to devices on a network

## Application Vs Application Layer Protocol

- Eg [[HTTP\|HTTP]] is used to retrieve web pages from remote servers
- Many implementations in different applications (Edge,Chrome etc)

**All of them use the same [[HTTP\|HTTP]] protocol**

