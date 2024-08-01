---
title: "Change Time Zone of Azure Virtual Machines"
pubDate: 2021-02-21
intro: How to change the time zone on an Azure VM.
author: dg
tag: Microsoft, Azure
image: ../../assets/azure-baseline.jpg
---
I noticed while working on a project that all my VM's in Azure were set to the UTC timezone. Time synchronization is critical in domain-based environments and I like to avoid issues cropping up if I can help it.

I tried the “normal” process to change the timezone for a Windows server but found it doesn’t work as expected. You can change the time zone by right-clicking on the clock and selecting “Adjust Date and Time”. If you change the time zone here, it doesn’t do anything (at least it didn’t when I did it). It may also change for a short period and then revert to UTC.

PowerShell to the rescue! This change will ensure the timezone change will stick, even if the VM is deallocated and reallocated.

To see all options available run the following command: We can see that by

```python
Get-TimeZone -ListAvailable
```

This lists every zone possible To filter your results, run the following command:

```python
Get-TimeZone -ListAvailable | where ({$_.Id -like "Pacific*"})
```
Now you can use the "Id" to set the timezone of your choice:

```python
Set-TimeZone -Id "Pacific Standard Time"
```