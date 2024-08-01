---
title: "Reset Fortigate Firewall Without Console Cable"
pubDate: 2022-07-28
intro: How to reset fortigate firewall with no console cable.
author: dg
tag: Networking, Fortinet
image: ../../assets/fortinet.jpg
---

I got a call today from a colleague who was on site and needed to factory reset a Fortigate 60E but didn't have a serial to USB cable. I immediately thought of how often I take having a console cable and serial to USB cable for granted.

If you have the proper tools, performing a factory reset is pretty straightforward:

* Login in via SSH
    
* Enter the following command and confirm
    

```python
#exec factoryreset  
*This operation will reset the system to factory default!
Do you want to continue? (y/n)*
```

After that, the system will reboot and you're set. In this case, we didn't have the luxury of the console. I naturally told him to press the reset button. He told me he had tried that and it did not work.

I performed research and I landed on a forum post where someone mentioned that the firewall has to be reset within the first 20-30 seconds of the device booting up. I was initially confused about the term powering *on*. I had my colleague power the device on and then after 20-30 seconds hit reset. This did nothing.

Upon further research, I found the reset button needs to be pressed within the first 20-30 seconds after\* the device has fully booted up\*. With this being the case, the sequence of events is as follows:

* Unplug the power.
    
* Watch and wait for the LEDs to start to blink (LAN, WAN and STA LEDs).
    
* 5 seconds after the STA LED blinks, press the small reset button at the back using a paper clip, keeping it pressed until you see the LEDs blink orange, then red.
    
* At this stage, you can release the button.
    

Once this is performed you have manually factory-reset your Fortigate firewall!