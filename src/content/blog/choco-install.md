---
title: "How to Install Chocolatey on Windows"
pubDate: 2024-05-21
intro: How to get Chocolatey up and running quickly on Windows.
author: dg
tag: Microsoft, Windows
image: ../../assets/choco.jpg
---

# Introduction

I recently worked with a colleague of mine and he ran into some issues with installing Chocolatey. I decided to do a write up on how to get it up and running quickly.

## What is Chocolatey Anyway?  

Chocolatey, often referred to as Choco, is a free, open-source package manager for Windows, similar to Apt or DNF in the Linux ecosystem. It allows you to install software via the Windows command line, handling the download, installation, and update process automatically. Linux users are typically familiar with this type of package management system.

Some may wonder, “Why use a program like this when we can just download the .exe or .msi files and install the software ourselves?”

That's a great question! Here are some reasons why:

* Streamlined Installation and Updates: When setting up a new operating system and needing multiple programs, you would typically search for each installer, download it, install it, and regularly check for updates. Chocolatey automates this entire process, especially when using automatic mode.
    
* Convenience and Speed: Instead of hunting for executable installers, you can use Chocolatey to install programs via the command line, making the process much quicker and more convenient.
    
* Version Control: Chocolatey allows you to manage the application versions you need. Often, downloading an executable directly gives you the latest version, which may not always be what you want.
    
* Unified Command Usage: Chocolatey offers clear, simple commands that are nearly identical to those used in other package management systems, making it easy to learn and use.
    

# **Install Using Powershell**

When installing the software via PowerShell, we must ensure the local *Get-ExecutionPolicy* is not set to restricted. Chocolatey suggests using *Bypass* to bypass the policy to get things installed or *AllSigned* for increased security.

First, we need to run the *Get-ExecutionPolicy*. If it returns *Restricted*, then we need to run one of the two commands below.

```powershell
Set-ExecutionPolicy AllSigned
```

OR

```powershell
Set-ExecutionPolicy Bypass -Scope Process
```

Now run the following command in the Windows shell.

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1')) 
```

If there are no errors, Chocolatey will be installed. We can verify the installation using the *choco* or *choco -?* command.

# **Verify Installation**

To verify that Chocolatey is installed, we will use the choco command.

```powershell
C:\WINDOWS\system32>choco
 Chocolatey v0.10.15
 Please run 'choco -?' or 'choco  -?' for help menu.
```

All done! Chocolatey is installed!