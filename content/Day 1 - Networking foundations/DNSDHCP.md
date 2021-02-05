---
title: "DNS/DHCP"
draft: false
weight: 50
pre: 
---

DNS stands for Domain Name System and it is used in our everyday tasks without even realising it. DNS can be compared to an address book since it is a directory of mappings between names and IP addresses and allows hosts to reach endpoints such as URLs or other machines.

<img src='/images/dns.png' width='500px'>


For example, when we browse a page and hit an URL, this is what happens:


DNS uses a hierarchy to manage the different types of servers.

<img src='/images/dnshierarchy.png' width='500px'>

When using DNS, the URL or name of a server is read from right to left, the root being the highest in the hierarchy and represented by a ".".

Based on this hierarchy, there are several types of DNS servers:
- The Root servers, which sit at the top and handle all the queries to .com, .net. .io, etc..
- The Authoritative servers, which own specific domains such as google.com, amazon.com, aws-cloudops.com, etc..
- The DNS resolvers, which handle the local DNS requets by doing recursive resolution to the Root and Authoritative servers in order to get the response back to the asking client machine


DNS stores different types of DNS records in its mapping directory, but there are only a few common ones that you will ever used:
- A record (Address) - maps a name to an IP address (i.e. bob.com -> 10.1.1.4)
- PTR record (Pointer) - maps an IP address to a name (i.e. 10.1.1.4 -> bob.com)
- CNAME record (Canonical Name) - maps a name t a name (i.e. network.bob.com -> something.else.com)
- NS record (Name Servers) - indicates the authoritative servers for the domain
- SOA record (Start of Authority) - provides information about the domain



What;s DHCP?
How does it work with DNS?
Give example of home network, or VoIP phone.









