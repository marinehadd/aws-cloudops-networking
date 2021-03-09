---
title: "Route53"
draft: false
weight: 55
pre: 
---

**Amazon Route 53** is a Domain Name System (DNS) web service. Route 53 provides three main functions:

* **Domain registration**: Route 53 allows you to register a **domain name** for your website, such as _example.com_. This domain name can be used by the users to access your website.

* **DNS service**: an EC2 instance has an IP address assigned to it (i.e. _10.0.0.42_). In order to connect to it, you would need to remember the whole IP address. Route 53 translates domain names, such as _example.com_, into IP addresses, such as _10.0.0.42_. Therefore, you could access your website by using the domain name instead of having to remember the whole IP address. This is the same concept as for traditional networking.

* **Health checking**: Route 53 uses health checks to monitor the health of your resources (such as EC2 instances or ELB). Optionally, you can receive notifications when your resources fail the health checks.

<img src='/images/how-route-53-routes-traffic.png'>


By default, AWS provides each VPC with a local DNS resolver, the .2 reserved IP address mentioned previously. This resolver allows resources inside the VPC to obtain a DNS name and to query other hosts.

As we discussed in Day 1, a DNS resolver is provided by a DHCP set. In AWS, there is a DHCP Option configured by default on each VPC, which contains details about the DNS servers provided by AWS.

So, alternatively, if you want to use another DNS server, you can just create a DHCP set with your DNS servers and apply that set to the VPC. In that case, all instances in this VPC will query all DNS requests to this new set of DNS resolvers.


Route 53 can route the traffic to the resources following routing policies depending on different needs:

* **Simple routing policy**: when you have a single resource, such as a web server that serves a website. 

* **Failover routing policy**: when you want an active-passive failover.

* **Geolocation routing policy**: when you want to route traffic based on the location of your users.

* **Geoproximity routing policy**: when you want to route traffic based on the location of your resources.

* **Latency routing policy**: when you have resources in multiple AWS Regions and you want to minimize latency.

* **Multivalue answer routing policy**: when you want Route 53 to respond to DNS queries with up to eight healthy records selected at random.

* **Weighted routing policy**: when you want to route traffic to multiple resources in proportions that you specify.

