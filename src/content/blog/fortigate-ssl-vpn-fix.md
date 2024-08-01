---
title: "Resolve SSL VPN Disconnects- Fortinet"
pubDate: 2020-03-03
intro: How to resolve SSL VPN disconnects with Fortinet firewalls.
author: dg
tag: Networking, Fortinet
image: ../../assets/checklist.jpg
---

I have performed a couple of Fortinet SD-WAN implementations and have been thoroughly impressed with them. It's fairly straightforward to set up and quite powerful.

Most of my clients utilize the SSL VPN functionality built in and I noticed that the VPN would disconnect randomly about 3-5 minutes after connecting. I did some research on this and found there are two commands you need to run to resolve the issue.

It's worth noting I am running at 6.0.1 and later. I believe these commands are different for older firmware versions. It's also possible this is resolved in 6.2.x releases but I haven't done much research on 6.2.

Essentially when you have two or more interfaces connected to the internet (SD-WAN) your session might become corrupt and not route traffic properly or cause your session to disconnect. The commands below ensure that WAN1 (Primary WAN) is the default for SSL VPN and that your sessions will not disconnect.

Fortinet commands-

```bash
config vpn ssl settings
    set source-interface wan1
end

config system interface
    edit wan1
        set preserve-session-route enable
    next
end
```