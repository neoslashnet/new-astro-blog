---
title: "AWS Geolocation Policy vs. Geoproximity Policy"
pubDate: 2024-02-27
intro: A quick look at two Route 53 routing policies.
author: dg
tag: AWS, Cloud
image: ../../assets/awsgeo.png
---

# Introduction

Last week I sat the AWS SysOps Administrator Associate exam. While studying for it, I kept getting these two routing policies confused. The words "geoproximity" and "geolocation" sound similar, but when it comes to routing traffic, they mean two different things.

Routing policies are a key part of managing cloud infrastructure, as they define how traffic gets directed to your resources across different locations. Understanding the differences between common policies like geolocation and geoproximity routing is essential to ensuring your applications are available, performing well, and localized for your end users.

Let's dive in and take a quick look at these two routing policies.

## Geolocation Routing Policy

A geolocation routing policy is what you use when you want to route traffic based on the location of your users. Most businesses these days have users all over the world, and they want to serve content to those users as fast as possible. A geolocation routing policy allows you to allocate the resources that serve your traffic based on the location that users' DNS queries originate from.

With geolocation routing, you can localize content and restrict the distribution of content to only the locations in which you are able or allowed to distribute. You can also balance the traffic load across endpoints in a predictable way.

For example, say you have servers in Oregon and New York, and many of your users are in California. A geolocation routing policy might send those California users to your Oregon server so you can serve them content specific to the West Coast of the US.

## Geoproximity Routing Policy

A geoproximity routing policy is what you use when you want to route traffic based on the location of your resources, or shift traffic flow between resources. This policy allows you to direct users to different servers, even though those servers might be further away, using something called a *bias.*

Take the previous example. Let's say you have servers in Oregon and New York, and users in California, but your New York servers are larger and can handle more traffic than the Oregon servers. You might use a geoproximity routing policy to direct a portion of the California users to the New York server. Another way of thinking about it is Geoproximity routing is like creating a sphere of influence for your resources.

# Conclusion

In summary, geolocation routing focuses on the location of your users and is ideal for localizing content and predictable load balancing. Geoproximity routing instead focuses on routing traffic based on the location and capacity of your resources in order to shift traffic between them as needed. Keeping these key differences in mind will help you apply the right routing policy for your infrastructure needs.