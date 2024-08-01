---
title: "Enable RDP From CMD Line"
pubDate: 2021-04-18
intro: Quickly enable RDP From CMD prompt.
author: dg
tag: Microsoft
image: ../../assets/saas.jpg
---
I ran into a situation this morning where I needed to quickly enable RDP on a remote machine. Sysinternals to the rescue!

```c
psexec -u domain\administrator -p "P@ssw0rd" \\remotecomputername.domain.com reg add "hklm\system\currentcontrolset\control\terminal server" /f /v fDenyTSConnections /t REG_DWORD /d 0
```

```c
psexec -u domain\administrator -p "P@ssw0rd" \\remotecomputername.domain.com netsh firewall set service remoteadmin enable
```