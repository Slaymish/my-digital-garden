---
{"dg-publish":true,"permalink":"/nwen-243-project-1/"}
---

Related: [[NWEN241/NWEN241 MOC\|NWEN241 MOC]]
Contents: [[NWEN243 MOC\|NWEN243 MOC]]
[Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/NWEN243_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 25-07-2023
***

# Project 1

PublicIPs: 52.23.167.1    
PrivateIPs: 172.31.81.8

```
burkehami@ip-172-31-81-8:~$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc fq_codel state UP group default qlen 1000
    link/ether 12:14:96:6f:4f:b1 brd ff:ff:ff:ff:ff:ff
    inet 172.31.81.8/20 metric 100 brd 172.31.95.255 scope global dynamic eth0
       valid_lft 2854sec preferred_lft 2854sec
    inet6 fe80::1014:96ff:fe6f:4fb1/64 scope link 
       valid_lft forever preferred_lft forever
```

## Q1

a) `eth0`
b) `12:14:96:6f:4f:b1`
c) `00010010 00010100 10010110 01101111 01001111 10110001`
d) 48 bits
e) `ff:ff:ff:ff:ff:ff`

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
11111110100000000001000000010100100101101111111111111110011011110100111110110001

80 bits long
```