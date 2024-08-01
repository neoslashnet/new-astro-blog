---
title: "Configure DHCP Scopes for separate VLANs- Cisco"
pubDate: 2019-06-16
intro: How to configure DHCP Scopes for separate VLANs- Cisco.
author: dg
tag: Networking, Cisco
image: ../../assets/checklist.jpg
---

This comes up often enough on core switches and routers. Below is how to configure four VLANs, VLAN interfaces, and DHCP scopes for each VLAN.

**The management VLAN will not have a DHCP scope. Typically you assign static IP addresses on your management VLAN.**

```bash
!
vlan 1010
name servers
!
vlan 1020
name users
!
vlan 1030
name lab
!
vlan 99
name management
!

interface vlan 1010
ip address 10.100.10.1 255.255.255.0
!
interface vlan 1020
ip address 10.100.20.1 255.255.255.0
!
interface vlan 1030
ip address 10.100.30.1 255.255.255.0
!
interface vlan 99
ip address 10.100.99.254 255.255.255.0
!

ip dhcp pool vlan1010
   network 10.100.10.0 255.255.255.0
   domain-name test.local
   dns-server 4.4.4.2 4.4.4.1
   default-router 10.100.10.1

   lease 3
!
   ip dhcp pool vlan1020
    network 10.100.20.0 255.255.255.0
    domain-name cisco.com
    dns-server 4.4.4.2 4.4.4.1
    default-router 10.100.20.1

   lease 3
!
 ip dhcp pool vlan1030
    network 10.100.30.0 255.255.255.0
    domain-name cisco.com
    dns-server 4.4.4.2 4.4.4.1
    default-router 10.100.30.1

   lease 3
   !
```