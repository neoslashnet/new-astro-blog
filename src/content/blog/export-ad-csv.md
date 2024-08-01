---
title: "Export AD Audit details to a CSV File"
pubDate: 2019-06-20
intro: Learn how to export AD Audit details to CSV.
author: dg
tag: Networking, Fortinet
image: ../../assets/4393.jpg
---

This is a very useful script I wrote to generate a .csv that shows valuable information from Active Directory.

```bash
$OutputPath = "c:\\support\\users.csv"  
  
$Year = "2019"  
  
$filename = "$($Year)\_users.csv"  
  
$YearUsers = Get-ADUser -Filter  {(Enabled -eq "True")} -Properties created, lastlogondate,passwordlastset,passwordneverexpires  
  
$YearUsers | select name, samaccountname, created,lastlogondate,passwordlastset,passwordneverexpires |  

Export-Csv -Path $OutputPath$filename -NoTypeInformation -Force