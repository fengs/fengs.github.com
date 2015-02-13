---
layout: post
title: "Setting up Custom Domain Name with Github Pages and Amazon Route 53"
description: ""
category: "technical"
tags: [DNS,Github Pages, AWS, Custom Domain, Registar]
---
{% include JB/setup %}

Amazon recently started offering [domain name registration](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/CreatingNewDNS.html) through the Amazon Route 53 from AWS (with partner Gandi). I did some research and people are recommending it over registration with GoDaddy. A .com top level domain costs $12/year. Pricing is clear, no hidden fees, privacy protection included. 5-year cost of $60 is about the same with Godaddy, which has a lower price for the first year but charges for privacy protection and various other services. I'm not going to use the web hosting of Godaddy anyway. So why not choose Amazon for its known reliability and high availability?

Following the [documentation](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/CreatingNewDNS.html), go to the Amazon Route 53 console, and do a name check.

![](../../../../../Fig/domain_check.jpg)

This is the fun part actually. I quickly gave up my favorite website name candidates, as unsurprisingly, they are all taken (a touch of sadness here). It seems every possible combination has been came up with then claimed. There were millions of people before you. Whatever you can think of, then could have, too. Even with homonyms, descendants, prefixes/suffixes, concatenations, all taken.

To a point, I got so frustrated that I started trying a series of polygons:

- triangle
- square
- pentagon
- hexagon
- ...

not available until tetradecagon. Send my respect to the anomymous owner of tridecagon.com. I was going to try the 14 Bravais lattice types of crystallography had I not stopped there.

A rule of thumb is always sticking to the `.com` extension. It's the highest ranked and most recognized (by search engines). `.org` and `.net` are not for you unless you are a non-profit organization. `.us` costs several times higher, requires you to be in United States but does not bring any advantages associated with the restrictions. `.info` are flagged for spammers as they stock thousands of cheap `.info` names.

So keep brainstorming. Fortunately my name is not taken. So I registered it for my Github blog. $12/year flat rate. You'll need to fill your contact information especially a valid email address. Beginning January 1st, 2014, ICANN requires that registrars verify that domain contacts can be reached. By default the contact information is protected. Therefore in whois lookup your email/phone/address is replaced by Gandi's. Amazon sent a address verification email minutes later. The registration is completed after clicking it.

Next step is to direct my Github blog to the custom domain name. They have a nice [documentation](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages/). Basically you'll need to do two things:

First, create a `CNAME` file under `yourname.github.com` repo of github, which is a one-liner of your domain:

    yourname.com
    
No `www.` needed. If you do put `www.yourname.com` github will figure out and redirect properly nevertheless, as explained [here](https://help.github.com/articles/tips-for-configuring-a-cname-record-with-your-dns-provider/). The difference is `yourname.com` is a top-level domain (TLD), while `www.yourname.com` is a subdomain.

The next is to go to Amazon Route 53 console, and create an `A` record:

> 192.30.252.153  
> 192.30.252.154

as explained [here](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider/).Then another `CNAME` record redirecting `www.yourname.com` to `yourname.github.io`, the original Github blog address. Here `www.` is necessary as Amazon does not allow TLD `CNAME`. Amazon's free `Alias` record can only point to their cloud (CloudFront distributions, ELB load balancers, or Amazon S3 buckets) thus the only choice is a `CNAME` record. It is not free but the price is ecominical, $0.4/million queries. See [pricing of Route 53](http://aws.amazon.com/route53/pricing/). So far I have spent $12 on registration, $0.50 for 1 host zone and $0.01 for 134 queries. I'm not going bankrupt for expenditure on queries unless I was being attacked.

I'd be happy to spend on traffic. Who'd not?

![](../../../../../Fig/route_53_billing.jpg)

I have not used other usage report/explorer of AWS. Hmm, lots of thing to try yet.






