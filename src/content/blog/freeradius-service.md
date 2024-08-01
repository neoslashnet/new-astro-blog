---
title: "Freeradius service will not start"
pubDate: 2021-02-02
intro: Troubleshoot when the Freeradius service will not start on your server.
author: dg
tag: Linux
image: ../../assets/checklist.jpg
---
Earlier today I made a simple change to a freeradius server at one of my clients. After making this change, I attempted to restart the service. I received the following error-

```python
root@ucs:~# systemctl restart freeradius
Job for freeradius.service failed because the control process exited with error code.
See "systemctl status freeradius.service" and "journalctl -xe" for details.
```

This created an issue for me as this radius server handles the authentication for a VPN with MFA.

Based on the error message, I ran the following command-

```python
journalctl -xe
```

Which showed me the following output-

```python
/etc/freeradius/3.0/mods-config/files/authorize[222]: Parse error (check) for entry myusername: Expected end of line or comma
```

One of the changes I made was a password change for myusername. After checking the error message, I realized you cannot have the \* symbol as the last character in the password. This throws off freeradius and will not allow the service to start. After adjusting this I was able to start the service and keep the login working.