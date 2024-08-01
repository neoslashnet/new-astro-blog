---
title: "Quick SNMP Configuration on Cisco switch and router"
pubDate: 2020-03-10
intro: SNMP Configuration on Cisco switch and router.
author: dg
tag: Networking, Cisco
image: ../../assets/checklist.jpg
---
Quick SNMP Config for a Cisco Router or Switch.

Log into your router or switch.

```bash
configure terminal
!
Use the command below to add a Read-Only community string:
!
snmp-server community public RO
!where "public" is the Read-only community string.
!To add a Read-Write Community string, use the command below:

!snmp-server community private RW
!where "private" is the Read-write community string.
!Exit the configuration mode and save the settings:
exit
!
write memory
!
Building configuration...
[OK]
Router#
```