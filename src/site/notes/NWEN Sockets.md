---
{"dg-publish":true,"permalink":"/nwen-sockets/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN MOC\|NWEN MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Whats a socket?

What you need to know to allow the two procceses on a network to communicate?
- IP address
- Port

<h3 align="center">
IP Address + port == socket
</h3>


# Port numbers
- Each host has 65,536 ports
- Ports 0-1023 requires priviledges
- Some ports are reserved
	- 20,21 : FTP
	- 80,443 = http/https



# Create a interface between app & network
- App creates socket
- Socket type dictates style of communication
	- TCP (transmission control protocol)
		- Reliable
		- Connection oriented
	- UDP (user datagram protocol)
		- Best effort
		- Connectionless