---
{"dg-publish":true,"permalink":"/nwen-sockets/"}
---

Related: #programming 
Contents: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN241_2023T1/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 27-02-2023
***

# Whats a Socket?

What you need to know to allow the two procceses on a network to communicate?
- IP address
- Port

<h3 align="center">
IP Address + port == socket
</h3>

# Port Numbers

- Each host has 65,536 ports
- Ports 0-1023 requires privileges
- Some ports are reserved
	- 20,21 : FTP
	- 80,443 = http/https

# Create a Interface between App & Network

- App creates socket
- Socket type dictates style of communication
	- [[TCP (transmission control protocol)\|TCP (transmission control protocol)]]
		- Reliable
		- Connection oriented
	- [[UDP\|UDP]]
		- Best effort
		- Connectionless

# TCP Server Overview
{ #02aff4}


1. Create a socket with socket()
2. Bind the socket to an address using bind()
3. Listen for connections with  listen()
4. Accept a connection with accept()
5. Send and receive data

```C
// step 1
//int socket(int domain, int type, int protocol); - method prototype

int fd = socket(AF_INET,SOCK_STREAM,0);

if(fd == -1){ // if not error
	printf("Error creating socket");
	exit(0);
}

// step 2
// int bind(int sockfd, const struct sockaddr *addr, socklen_t addrLen); - method prototype
// struct sockaddr contains the ip addr and port (though generic)
// Use struct sockaddr_in - for internet

struct sockaddr_in addr;
addr.sin_family = AF_INET;
addr.sin_port = htons(1234); // port 1234
addr.sin_addr.s_addr = INADDR_ANY; // any address

if(bin(fd, (struct sockaddr *)&addr, sickof(addr))<0){
	printf("Error binding socket");
	exit(0);
}

// step 3
// int listen(int sockfd, int backLog); - method prototype
// backLog = max num of pending connections allowed for socket

if(listen(fs,SOMAXCONN)<0){
	printf("Error listening to conections");
	exit(0);
}

// step 4

```

# TCP Client Overview

1. Create a socket with socket()
2. Connect the socket to the address of the server with connect()
3. Send/Receive data
