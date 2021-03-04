---
title: "DNS/DHCP"
draft: false
weight: 50
pre: 
---


**Domain Name System (DNS):**
---

DNS stands for Domain Name System and it is used in our everyday tasks without even realising it. DNS can be compared to an address book since it is a directory of mappings between names and IP addresses and allows hosts to reach endpoints such as URLs or other machines.

<img src='/images/dns.png' width='500px'>

The full name of a server or endpoint is made of a hostname and the domain in which it sits. It is called a Fully Qualified Domain Name (FQDN) and is used for DNS resolution.

<img src='/images/fqdn.png' width='800px'>

<h4> Hierarchy </h4>

DNS uses a hierarchy to manage the different types of servers.

<img src='/images/dnshierarchy.png' width='900px'>

When using DNS, the URL or name of a server is read from right to left, the root being the highest in the hierarchy and represented by a ".".

Based on this hierarchy, there are several types of DNS servers:
- The Root servers, which represent the "." of a domain
- The Top Level Domain (TLDs), which are authoritative for .net, .com. .io, etc..
- The Authoritative servers, which own specific domains such as google.com, amazon.com, aws-cloudops.com, etc..
- The DNS resolvers, which receive DNS queries and handle caching and resolution.

<h4> Resolution Types </h4>

DNS resolution can be either iterative or recursive.

In an iterative resolution, the local computer DNS resolver handles the full DNS resolution journey.

<img src='/images/dnsiterative.png' width='800px'>

In a recursive resolution, the DNS resolver/caching server handles the full DNS resolution journey.

<img src='/images/dnsrecursion.png' width='800px'>


Once bob.com is resolved, the data will be cached into the local DNS cache so that next time it is queried, the resolution does not need to happen again, until the data expires.
The time length of a cached resource is called a Time-To-Live (TTL). A TTL is a setting configured on a DNS resource to allow DNS caching.

<h4> DNS Records </h4>

Those name/IP mappings stored in DNS servers are called resources or records.

DNS stores different types of DNS records in its mapping directory, but there are only a few common ones that you will ever used:
- A record (Address) - maps a name to an IP address (i.e. bob.com -> 10.1.1.4)
- PTR record (Pointer) - maps an IP address to a name (i.e. 10.1.1.4 -> bob.com)
- CNAME record (Canonical Name) - maps a name to a name (i.e. network.bob.com -> something.else.com)
- NS record (Name Servers) - indicates the authoritative servers for the domain
- SOA record (Start of Authority) - provides administrative information about the domain
- MX record (Mail Exchange) - indicates which mail servers are used to send emails to the domain



**Dynamic Host Configuration Protocol (DHCP):**
---

DHCP stands for Dynamic Host Configuration Protocol and is used to dynamically allocate IP addresses to clients in a network.

The way it works:
- A new client connects to a network
- The client requests the DHCP server a new IP address in this network
- The DHCP server leases an IP address to this client for a specific duration
- When the client disconnects, the IP is released in the DHCP pool. If the client remains and the duration has expired, the lease is renewed.

We call that process, DORA (Discover, Offer, Request, Acknowldge).


<img src='/images/dora.png' width='600px'>


When a DHCP server leases an IP address, it doesn't only provide the IP but also information around it such as the router gateway of the network and the DNS servers.
In other cases where a client would require other services such as a FTP server for example, this would also be provided in the lease. These additional information are called DHCP Options, and each option corresponds to a number.

***Examples:***

- Option 1 = subnet mask
- Option 3 = router gateway
- Option 6 = DNS servers
- Option 51 = lease duration time











