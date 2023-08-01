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

![400][SCR-20230801-lxcz-2.png]

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
256
```

d)

```
11000111001111110111110111
```

e)

```
Private ip:
11111110100000000001000000010100100101101111111111111110011011110100111110110001

80 bits long
```

## Q3

a)

```
172.31.81.8/20

The /20 means the first 20bits of the IP address is the network bits.

10000011011101111110 01010 is the binary representation of the IP. 25 bits in total

So network = 10000011011101111110
And host = 01010
```

b) * dont think correct

```
172.31.81.0
```

c) ***

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
255.255.240.0
```

b)

![SCR-20230801-mgwj-2.png](/img/user/SCR-20230801-mgwj-2.png)

```
172.31.95.255
```

c) *

```
In the last octet of the private IP in binary, set all of the host bits to 1.

It can be obtained from the IP address and netmask by
```

## Q5

a)

![400][SCR-20230801-mjlm-2.png]

```
This is the only device on the LAN that I know about. The IP and MAC address are both the routers.
```

b) **

![400][SCR-20230801-mjzd-2.png]

## Q6

a)

![400][SCR-20230801-mksh-2.png]

```
IP1 = 172.253.122.136
```

b)

![300][SCR-20230801-mlnp-2.png]

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

![400][SCR-20230801-ncta-2.png]

b)

![400][SCR-20230801-nfvv-2.png]

c)

```
commons links at start/end? Reason why
```

## Q8

a)

![400][SCR-20230801-nelc-2.png]

b)

![400][SCR-20230801-nfos-2.png]

c)

```
commons links at start/end? Justify
```

## Q9

```

```