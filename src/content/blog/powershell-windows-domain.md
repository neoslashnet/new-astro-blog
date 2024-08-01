---
title: "Add a machine to Microsoft Windows Domain with PowerShell"
pubDate: 2019-06-03
intro: Quickly enable RDP From CMD prompt.
author: dg
tag: Microsoft, Powershell
image: ../../assets/saas.png
---
I've been trying to learn more about PowerShell and use it more frequently. I recently decided to script adding a server to a domain via PowerShell.

Here is the command-

```powershell
add-computer –domainname ad.contoso.com -Credential AD\\adminuser -restart –force
```

Once entered you will be prompted to enter admin credentials.