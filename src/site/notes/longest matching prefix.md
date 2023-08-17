---
{"dg-publish":true,"permalink":"/longest-matching-prefix/"}
---


This is what IP is selected when it matches multiple entries in a [[Forwarding Table\|Forwarding Table]]

```
IP to Forward: 192.168.1.50

Forwarding Table:
192.168.1.0/24   Interface A
192.168.0.0/16   Interface B
192.168.1.32/27  Interface C

```

The **longest prefix** is 192.168.1.32/27, so the packet would be forwarded to Interface C.
