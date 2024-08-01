---
title: "Useful Fortinet HA Commands"
pubDate: 2020-03-19
intro: Useful Fortinet High Availability Commands.
author: dg
tag: Networking, Fortinet
image: ../../assets/fortinet.jpg
---

Over the past couple of months, I've had to configure HA (High Availability) on several Fortigate firewalls. During the setup process and troubleshooting, I found the commands below to be most useful.

```bash
get system ha
```

This command gives you all the details on your overall configuration. It shows the group id, mode, heartbeat interfaces, monitor interfaces, and other details such as whether encryption is enabled.

```bash
get system ha status
```

The next command gives you insight into the overall health of your HA configuration and tells you if the devices are in sync. If everything is working, you will see-

```bash
HA Health Status: OK  
Configuration status:  
  Masterserialnumber (Updated 1 seconds ago) in-sync  
  Slaveserialnumber (Updated 1 seconds ago) in-sync
```

Another key thing to look for with this command is the **"Master"** selection process is displayed. The output of the command will show you which device is the "Master" and how it was selected. Side note- If you want one unit to always be the "Master" you can use the following commands (In addition to priority)

```bash
config system ha 
set override enable 
end
```

The bit of information on this command is that it will list the operating cluster index of the device. Typically this is 0 for the "Master" unit and 1 for the "Slave". This comes in very useful for the next two commands.

If your devices are "Out of sync" you have a couple of options from the command line. First, you can use

```bash
execute ha manage 1
```

to manage your "Slave device". This is assuming your "Slave" device is out of sync for whatever reason. Once you execute this command you will see a login prompt. Log into the device and to force a sync use

```bash
execute ha synchronize start
```

After you perform a manual sync, you can use the previous commands to verify everything is working.