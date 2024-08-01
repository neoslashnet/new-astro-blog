---
title: "How to create multiple TXT records in AWS Route 53"
pubDate: 2021-02-12
intro: Quickly create multiple TXT records in AWS Route 53.
author: dg
tag: AWS, Cloud, DNS
image: ../../assets/checklist.jpg
---

Domain verification has become something everyone has to do to use certain services. For example, Microsoft 365. I ran into a little snag today and it wasn't as straightforward as I thought.

My customer already had and txt record in Route 53 for their spf. I had a request to add another txt record for another service to perform domain ownership/verification.

When I went to add the record, it would not allow me to use @ as the host as it created a new record @.domain.com instead of using the root-level domain name.

After researching this, I found the answer is to add the txt value into the already existing record in quotes underneath the existing value.

This is an example:

```python
"ms=M23445345"
"v=spf1 include:spf.protection.outlook.com -all"
```

The interesting part is when I did a dig and nslookup for txt records, the results show two different txt records.