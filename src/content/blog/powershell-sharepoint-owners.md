---
title: "PowerShell Script to Confirm SharePoint Online Site Owners"
pubDate: 2021-10-07
intro: Check Sharepoint owners with PowerShell.
author: dg
tag: Microsoft
image: ../../assets/ms.png
---
Earlier this week I had a request from a client that asked me for an export of all their SharePoint sites which included the site owner. This client has a large number of sites so I didn't want to take screen captures manually. I put together this PowerShell script to export a csv file. 

The exported csv file contains the following details: 

+ Owner
+ URL
+ Site Title

Here is the scripit! 

```js
#Variables for Admin Center
$AdminCenterURL = "https://site-name.sharepoint.com/"
$CSVPath = "C:\support\SiteOwners.csv"

#Get Credentials to connect
$Cred = Get-Credential

#Connect to SharePoint Online and Azure AD
Connect-SPOService -url $AdminCenterURL -Credential $Cred
Connect-AzureAD -Credential $Cred | Out-Null

#Get all Site Collections
$Sites = Get-SPOSite -Limit ALL

$SiteOwners = @()
#Get Site Owners for each site collection
$Sites | ForEach-Object {
    If($_.Template -like 'GROUP*')
    {
        $Site = Get-SPOSite -Identity $_.URL
        #Get Group Owners
        $GroupOwners = (Get-AzureADGroupOwner -ObjectId $Site.GroupID | Select -ExpandProperty UserPrincipalName) -join "; "      
    }
    Else
    {
        $GroupOwners = $_.Owner
    }
    #Collect Data
    $SiteOwners += New-Object PSObject -Property @{
    'Site Title' = $_.Title
    'URL' = $_.Url
    'Owner(s)' = $GroupOwners
    }
}
#Get Site Owners
$SiteOwners

#Export Site Owners report to CSV
$SiteOwners | Export-Csv -path $CSVPath -NoTypeInformation
```