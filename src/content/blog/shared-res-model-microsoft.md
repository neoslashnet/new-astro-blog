---
title: "Microsoft 365 Shared Responsibility Model"
pubDate: 2019-05-13
intro: Exploring the Microsoft 365 Shared Responsibility Model.
tag: Microsoft
author: dg
image: ../../assets/saas.jpg
---

# Introduction

One conversation I frequently have with clients regarding cloud services is helping them understand the shared responsibility model. There are often privacy concerns over their data or clients feel that simply throwing data into the cloud by default makes it secure. The line I always use is- **The cloud vendor is responsible for the cloud; you are responsible for what is in the cloud.** In this article, I explore the Microsoft shared responsibility model and what Microsoft is responsible for and what you, the customer is responsible for.

# Microsoft Shared Responsibility model

SaaS platforms like Microsoft 365 are great because they are extremely powerful and eliminate the need to deploy and manage software on your servers. That does not mean that SaaS solutions free you from having to manage security or the data stored within it. Again, you are responsible for security in the cloud.

This is where the shared responsibility model comes into play. The provider delegates many security-related matters such as data protection and security to their customers through the shared responsibility model. Here’s the [official link](https://www.microsoft.com/security/blog/2018/06/19/driving-data-security-is-a-shared-responsibility-heres-how-you-can-protect-yourself) on how Microsoft 365’s shared responsibility model works and what you should know if you deploy Microsoft 365 in your business.

# What Microsoft Is Responsible For

As part of the Microsoft 365 SaaS platform, Microsoft manages and guarantees the following:

* **Uptime:** Microsoft guarantees maximum uptime for the infrastructure and software that hosts Microsoft 365.
    
* **Data replication:** To ensure high availability and reliability for data stored in Microsoft 365, Microsoft replicates it across multiple locations. Note, however, that data replication by Microsoft does not protect against accidental data deletion by users: If you delete a file, all copies of it on Microsoft’s infrastructure will be deleted.
    
* **Access control:** Available access controls for Microsoft 365 include multi-factor authentication in addition to basic password-based authentication.
    
* **Infrastructure setup and management:** Microsoft configure and manage the infrastructure that hosts Microsoft 365. Management includes protecting against electrical failures, natural disasters and other problems that could disrupt service availability.
    
* **Physical access:** Microsoft protects unauthorized access to the physical infrastructure that hosts Microsoft 365, which ensures that attackers cannot gain access to data stored in the system by physically accessing the servers hosting it.
    

As you can see, Microsoft manages the aspects of the security of Microsoft 365, as well as related issues, such as data and service availability.

# What You Are Responsible For

The primary responsibility of Microsoft 365 customers lies in securing the data you store and manage on the Microsoft 365 platform. Although Microsoft manages the infrastructure and services that host that data, users need to guard against risks such as the following:

* **Accidental data deletion:** Microsoft provides tools like the Microsoft 365 recycling bin to mitigate the risk of accidental data loss, but they only store deleted data temporarily. I always recommend using a third-party cloud backup system with a daily schedule and retention policy.
    
* **Internal and external attacks:** A malicious employee could deliberately delete data, or a third party that gains access to your Microsoft 365 resources could encrypt it and hold it for ransom as part of a ransomware attack.
    
* **Regulatory compliance:** Users must ensure that any sensitive data that they store in Microsoft 365 is managed in ways that comply with regulatory policies that govern that data. Microsoft’s Litigation Hold feature can help manage data subject to litigation holds, but that is only one regulatory issue at stake.
    
* **Data retention:** Responsibility lies with users to ensure that they retain data in Microsoft 365 for the periods specified by any applicable laws or internal company policies. They may also need to delete certain data after a specified period. Microsoft automatically deletes data inactive accounts after ninety days, which may not be long enough to ensure compliance with data retention policies.
    

In closing, while Microsoft keeps your infrastructure available, you are responsible for keeping your data secure and compliant.