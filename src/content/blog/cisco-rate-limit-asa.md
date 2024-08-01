---
title: "How to rate limit a host with Cisco ASA"
pubDate: 2020-03-20
intro: How to rate limit a host with Cisco ASA.
author: dg
tag: Networking, Cisco
image: ../../assets/checklist.jpg
---
Do you have a host on your network using up all the bandwidth? Maybe an offsite backup device keeps sending GBs of data offsite?

In my case, I deployed an AWS Storage gateway in file gateway mode. This works perfectly for my use case but there are a couple of "Gotcha's" with the AWS file gateway versus a volume or tape library.

The main one is that you cannot schedule or rate limit the file gateway directly within the AWS Console. This is simply not built into the solution. To ensure the upload did not use all the bandwidth on the network, I used rate limiting on the Cisco ASA. Below is the configuration.

The first step is to create an ACL for the host (In this example the file gateway is 1.1.1.1). I am allowing all IP traffic to and from this host.

```powershell
access-list AWS-FileGW-Throttle extended permit ip host 1.1.1.1 any
access-list AWS-FileGW-Throttle extended permit ip any host 1.1.1.1
```

Next, you need to create a class map to match the ACL that was just created.

```powershell
class-map CM-AWSTHROTTLE
match access-list AWS-FileGW-THROTTLE
exit
```

After that, you need to configure a policy map that the ASA will use to police the traffic. In this example, I am rate-limiting the host to 10 Mbps with a burst rate of 1 Mbps.

```powershell
policy-map PM-AWSTHROTTLE
class-CM-AWSTHROTTLE
police output 10000000 1000000
police input 10000000 1000000
exit
```

Once these steps are complete you need to tie a service policy to the inside interface.

```powershell
service-policy PM-AWS-THROTTLE interface inside
```

That's it! Now go and check your network monitoring software/netflow and you'll see it is working!