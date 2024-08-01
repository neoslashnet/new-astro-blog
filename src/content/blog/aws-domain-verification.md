---
title: "GoDaddy Domain verification via DNS TXT record- AWS"
pubDate: 2020-05-11
intro: GoDaddy Domain verification via DNS TXT record in AWS.
author: dg
tag: AWS, Cloud, DNS
image: ../../assets/checklist.jpg
---
There's no question that AWS Route 53 is an extremely powerful service in the cloud. I've been using it frequently for about 6 months and recently found a small quirk while proving domain ownership.

I had to renew an SSL Certificate for a client where GoDaddy is not hosting the DNS zone. In AWS Route 53 there was already a TXT record at the root domain level for their SPF record. I added a new record with the @ symbol with the value GoDaddy provided. In this example, it's "26ug3xxxxxxxxxxxxxx". There for the new record was @.domain.com with the value "26ug3xxxxxxxxxxxxxx". Unfortunately, this did not work.

After some digging around online I found a forum post where someone had encountered the same issue. It turns out AWS Route 53 doesn't support having multiple TXT records at the root domain level. The way to resolve it is (in this case) to add another line to the preexisting record.

DNS Configuration

```bash
Name
domain.com

Value
"v=spf1 include:_spf.google.com ~all"
"26ug3xxxxxxxxxxxxxxxxxxx"
```