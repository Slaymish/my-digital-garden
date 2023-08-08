---
{"dg-publish":true,"permalink":"/nwen-243-project-1/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 25-07-2023
***

<https://ecs.wgtn.ac.nz/foswiki/pub/Courses/NWEN243_2023T2/ProjectsAndLabs/NWEN_243_Project_1.pdf>

# Project 1

## Q1

a) `eth0`
b) `12:14:96:6f:4f:b1`
c) `00010010 00010100 10010110 01101111 01001111 10110001`
d) 48 bits
e) `ff:ff:ff:ff:ff:ff`

![SCR-20230801-lxcz-2.png](/img/user/SCR-20230801-lxcz-2.png)

## Q2

a)

```
Public IPs: 52.23.167.1    
Private IPs: 172.31.81.8
```

b)

```
fe80::1014:96ff:fe6f:4fb1
```

c)

```
00110100 00010111 10100111 00000001

32 bits
```

d)

```
00110100 00010111 10100111 00000001
```

e) 

```
1111111010000000 0000000000000000 0000000000000000 0000000000000000 0001000000010100 1001011011111111 1111111001101111 0100111110110001


128 bits
```

## Q3

![SCR-20230801-lxcz-2.png](/img/user/SCR-20230801-lxcz-2.png)

a)

```
172.31.81.8/20

The /20 means the first 20bits of the IP address is the network bits.

10101100 00011111 01010001 00001000 is the binary representation of the IP. 32 bits in total

So network = 10101100 00011111 0101
And host = 0001 00001000
```

b) 

```
172.31.80.0 to 172.31.95.255
```

c) 

```
So 32-20 = 12
2^12 = 4096
4096 Total IP's
-2 for router and .0
= 4094 usable distinct IPs
```

## Q4

a)

```
Based on the CIDR notation which is /20, there are 20 network bits.
By setting all of these to 1, and the rest (the host bits) to 0, you get the netmask.


255.255.240.0
11111111111111111111000000000000
```

b)

![SCR-20230801-mgwj-2.png](/img/user/SCR-20230801-mgwj-2.png)

```
172.31.95.255
```

c) 

```
The broadcast address is the highest possible IP address.

This can be found by setting all of the host bits in IP address to 1.
You can use either CIDR notation or the netmask to find out how many bits are network bits. 

I converted the IP to binary:
10101100 00011111 01010001 00001000

Then set the host bits (last 12) to 1:
10101100 00011111 01011111 11111111

Convert to decimal:
172.31.95.255
```

## Q5

a)

![SCR-20230801-mjlm-2.png](/img/user/SCR-20230801-mjlm-2.png)

```
This is the only device on the LAN that I know about. The IP and MAC address are both the routers. Reachable means it is possible to send/recieve to.
```

b) 

![SCR-20230801-mjzd-2.png](/img/user/SCR-20230801-mjzd-2.png)

```
This shows that the default ip to route traffic to is 172.31.80.1. As shown in part(A), this is the router of the network this machine is on. Part A shows the MAC address of the router, which is important information so the sender and reciever knows if packets are designated for them.

'ip route list' shows what devices to route through, depending on the source IP. As theres only one other known device on the network, It is sending everything through 172.31.80.1. All of them use the eth0 wireless interface. 'proto dhcp' means that the route was obtained by DHCP. 'src 172.31.81.8' says what IP to use as source for packets sent from this machine. 'metric 100' is the cost assigned to the route. As they're all the same, this has no effect.
```

## Q6

a)

![SCR-20230801-mksh-2.png](/img/user/SCR-20230801-mksh-2.png)

```
IP1 = 172.253.122.136
```

b)

![SCR-20230801-mlnp-2.png](/img/user/SCR-20230801-mlnp-2.png)

```
IP2 = 142.250.74.142
```

c)

```
I took the average RTT

RTL_VM_IP1: 1.243ms
RTL_VM_IP2: 95.989ms
RTL_local_IP1: 91.646ms
RTL_local_IP2: 32.191ms
```

d)

```
The difference in the round trip time is likely because of the location of the VM/local computers in relation to the youtube server. IP1 is closer to the VM while IP2 in closer to the 'local' machine. The dns server they retrieved the IP from would have given them the closed server to them.
```

## Q7

a)

![SCR-20230801-ncta-2.png](/img/user/SCR-20230801-ncta-2.png)

b)

![SCR-20230801-nfvv-2.png](/img/user/SCR-20230801-nfvv-2.png)

c) **

```
Same:
- Hop 23 & hop 25 (IP1)


As shown in the above two traceroutes, my computer and the AWS machine didn't share any common links to IP1. This isn't very suprising as the location of my computer and the AWS instance is very different, so the path to get to the IP is likley to be different. If I ran it a few more times, I may find similar nodes for the last couple hops of the traceroute, at that is nearer to the end sever location. 
```

## Q8

a)

![SCR-20230801-nelc-2.png](/img/user/SCR-20230801-nelc-2.png)

b)

![SCR-20230808-mopq-2.png](/img/user/SCR-20230808-mopq-2.png)

c) **

```
commons links at start/end? Justify
```

## Q9

![400][SCR-20230805-skbz-2.png]![400][SCR-20230805-skgk-2.png]

```
I did a traceroute from the aws instance ecs.vuw.ac.nz. I repeated this and shown above, even the first hop is different (as well as others [eg 2,3 etc]). This shows the multiplicity of paths available between any two nodes.

The second time I ran it, it actully took fewer hops as well, from 21 to 19. This shows how it must have found a more efficent route to get there.
```

## Q10

![SCR-20230805-smfp-2.png](/img/user/SCR-20230805-smfp-2.png)

a) identify each packet, for each, specify: who is sending to who, and what its purpose is

```
tcpdump: listening on eth0, link-type ENlOMB (Ethernet), snapshot length 262144 bytes

09:18:40.146326 IP (tos 0x0, ttl 64, id 34387, offset 0, flags [none], proto UDP (17), length 71)
	172.31.81.8.46514 > 172.31.0.2.53: 4419+ [lau] A? www.wgtn.ac.nz. (43)

09:18:40.146455 IP (tos 0x0, ttl 64, id 26273, offset 0, flags [none], proto UDP (17), length 71)
	172.31.81.8.36508 > 172.31.0.2.53: 6971+ [lau] AAAA? www.wgtn.ac.nz. (43)

09:18:40.149695 IP (tos 0x0, ttl 255, id 30180, offset 0, flags [none], proto UDP (17), length 135)
	172.31.0.2.53 > 172.31.81.8.46514: 4419 4/0/1 www.wgtn.ac.nz. A 151.101.66.49, www.wgtn.ac.nz. A 151.101.130.49, www.wgtn.ac.nz 151.101.194.49, www.wgtn.ac.nz. A 151.101.2.49 (107)

09:18:40.173928 IP (tos 0x0, ttl 255, id 30181, offset 0, flags [none], proto UDP (17), length 155)
	172.31.0.2.53 > 172.31.81.8.36508: 6971 0/1/1 (127)
```

```
Packets 1-2 are DNS queries from client -> DNS server
Packets 3-4 are DNS responses from DNS server -> client

Responds with IP addresses and AAAA

```

b)

```

```

## Q11