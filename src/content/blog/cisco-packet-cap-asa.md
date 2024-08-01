---
title: "Packet Capture on Cisco ASA"
pubDate: 2021-03-04
intro: Perform packet captures on a Cisco ASA firewall.
author: dg
tag: Networking, Cisco
image: ../../assets/checklist.jpg
---
I've found that people sometimes get nervous running debug commands as well as captures. There are horror stories where you run a debug command and the firewall just locks up.

I have been doing quite a bit of troubleshooting on site-to-site VPN tunnels and have had to get some captures to confirm exactly what is happening.

Below is a sample command you can use to match the traffic that matches the host 1.1.1.1 which in my case is the VPN peer IP address.

```python
capture cap1 interface outside match ip host 1.1.1.1 any
```

Once the capture is configured you can view the capture by running the following command:

```python
show capture cap1
```

You should see some information similar to this:

```python
 2 packets captured
 
 1: 04:12:10.428093       192.168.10.10.34327 > 10.94.0.51.15868: S
    2669456341:2669456341(0) win 4128 <mss 536> Drop-reason: (acl-drop)
    Flow is denied by configured rule
 2: 04:12:12.427330       192.168.10.10.34327 > 10.94.0.51.15868: S
    2669456341:2669456341(0) win 4128 <mss 536> Drop-reason: (acl-drop)
    Flow is denied by configured rule
 2 packets shown
```

After you view the capture and don't need it anymore, you can clear all the captures on the ASA with the following command:

```python
clear capture /all
```