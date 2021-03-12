---
title: "FAQs"
chapter: false
weight: 110
---

**Subnetting Exercises Correction:**

- 192.168.0.5/16

***What is the binary address of 192.168.0.5?***
1100 0000.1010 1000.0000 0000.0000 0101

***What is the subnet mask?***
The subnet mask is /16 which equals to this binary address: 1111 1111.1111 1111.0000 0000.0000 0000 => 255.255.0.0

***What is the network ID?***
Since the subnet mask equals to /16, it means the network portion stops at the 16th bit of the IP address. Therefore the network portion is 192.168., and we complete it with zeros to get the ID => 192.168.0.0.

***What is the gateway router IP address?***
The gateway is the second IP address (or first usable) => 192.168.0.1.

***How many IP addresses in this network?***
<p>Maximum nb of bits = 32<br>
Subnet mask bits = 16<br>
Number of IP addresses = 2^(32-16)= 2^16 = 65 536<br>
Number of usable IP address = 65 536 - 2 = 65 534</p>


- 172.31.10.10/25

***What is the binary address of 172.31.10.10?***
1010 1100.0001 1111.0000 1010.0000 1010

***What is the subnet mask?***
The subnet mask is /25 which equals to this binary address: 1111 1111.1111 1111.1111 1111.1000 0000 => 255.255.255.128

***What is the network ID?***
Since the subnet mask equals to /25, it means the network portion stops at the 25th bit of the IP address. Therefore the network portion is 172.31.10., and we complete it with zeros to get the ID => 172.131.10.0.

***What is the gateway router IP address?***
The gateway is the second IP address (or first usable) => 172.31.10.1.

***How many IP addresses in this network?***
Maximum nb of bits = 32<p>
Subnet mask bits = 25<br>
Number of IP addresses = 2^(32-25)= 2^7 = 128<br>
Number of usable IP address = 128 - 2 = 126</p>


- 10.20.3.2/24

***What is the binary address of 10.20.3.2?***
0000 1010.0001 0100.0000 0011.0000 0010

***What is the subnet mask?***
The subnet mask is /24 which equals to this binary address: 1111 1111.1111 1111.1111 1111.0000 0000 => 255.255.255.0

***What is the network ID?***
Since the subnet mask equals to /24, it means the network portion stops at the 24th bit of the IP address. Therefore the network portion is 10.20.3., and we complete it with zeros to get the ID => 10.20.3.0.

***What is the gateway router IP address?***
The gateway is the second IP address (or first usable) => 10.20.3.1.

***How many IP addresses in this network?***
Maximum nb of bits = 32<p>
Subnet mask bits = 24<br>
Number of IP addresses = 2^(32-24)= 2^24 = 256<br>
Number of usable IP address = 256 - 2 = 254</p>



**What does a /16 mean?**

The /16 (or /17, 18, etc) is called a subnet mask and defines the size of a network. The number after the / represents the number of bits in the network portion of an IP address. Given 8 bits represent an octet, which represents a decimal number, a /16 would stop after the second octet of an IP address. In the same way, a /24 would stop after the third octet of an IP address given 24 bits equals to 3 times an octet (8 bits).
Example: 
* 10.1.1.1/16 -> Network portion = 10.1. (so the network ID will be 10.1.0.0)
* 10.1.1.1/24 -> Network portion = 10.1.1. (so the network ID will be 10.1.1.0)
* 10.1.1.1/8 -> Network portion = 10. (so the network ID will be 10.0.0.0)

**What are the reserved IPs and what is the difference with the gateway router IP?**

The reserved IPs in a traditional subnet (non AWS) are the following:
* first IP of the network (i.e. 10.1.1.0/24) = reserved for the network ID/Address
* last IP of the network (i.e. 10.1.1.255/24) = reserved for the broadcast IP

The router gateway IP address is not strictly reserved but is usually assigned to the second IP address (or first usable address) of the network (i.e. 10.1.1.1/24).

**How can I know how many subnets in a network?**

Let's pick an example : 

/24 = 24 bits = 1111 1111.1111 1111.1111 1111.0000 0000 => In the host portion we have 8 bits of space and 8 bits = 256
/25 = 25 bits = 1111 1111.1111 1111.1111 1111.1000 0000 => If we were using this /25 inside the host portion of a /24, it means we would only be using 1, and this bit is equal to 128.
However, given the /24 can accept up to 256 hosts and the /25 is only using half, it then means that we actually put 2x /25 (2x 128) in this /24.

Therefore : 1 x /24 = 2 x /25 

In real life, that means that we could for example configure our big network (or VPC in AWS) and then create 2 small subnets of /25 inside to dedicate to 2 different departments or applications.

The same logic applies to all subnet maks, i.e. 1 x /16 = 2 x /17 = 4 x /18 etc....

**What is the difference between a switch and a router?**

A switch works at L2 of the OSI and helps devices to communicate inside a network (i.e. 10.1.1.2 to 10.1.1.3). It does not understand IP addresses and will work using MAC addresses.

A router works at the L3 of the OSI and helps devices to communicate between different networks or to the Internet (anything that is not part of the local network).


**In a nutshell, what is a the difference between DNS and DHCP?**

DNS can be compared to an address book and is used to map names and IP addresses together. You are using DNS every time you're browsing a URL - your browser first asks a DNS server what is the IP address of the URL in order to redirect you to that URL.

DHCP is used to dynamically provide IP addresses. Every time you join a new network, you automatically get an IP address - this is thanks to DHCP which has detected you and leased you an IP. In addition to this IP, DHCP also gave you all the necessary information you will probabaly need such as your IP, your network, your router gateway, and your DNS servers for whenever you want to browse the Internet for example.

**Useful tools:**

To test connectivity between devices (i.e. your laptop and a server or even a website), you can use the PING command.
Example: *ping 10.1.1.1*    OR      *ping networking.aws-cloudops.com*

To check your network details, you can use IFCONFIG (for Linux/Mac) or IPCONFIG (for Windows) commands.

The above commands will give you your private IP address (from the network you are connected to). If you want to know your public IP address (the IP that the outside world sees), you can open a tab in your browser and type ***whatsmyip***.

To have a look at what routes your laptop has in its route table, you can use NETSTAT -RN (for Linux/Mac) or ROUTES (for Windows).

To check the route taken when sending traffic from an instance to another instance, you can use TRACEROUTE (for Linux/Mac) or TRACERT (for Windows):
Example: *traceroute 10.1.1.1* OR *tracert 10.1.1.1*

To resolve a name to an IP, or an IP to a name (that's when we talk about DNS), you can use the DIG (for Linux/Mac) or NSLOOKUP (for Windows) commands.
Example: *dig networking.aws-cloudops.com*      OR      *nslookup networking.aws-cloudops.com*


**What makes an instance public?**

For an instance to be public, it must have:
* a public IP address
* a route table with a default route to an Internet Gateway

**How can a private instance use to download resources (software, patches, updates..) from the Internet?**

A private instance can use a NAT Gateway to access resources to the Internet while remaining private (not accessible from the Internet).

**Can a subnet span across 2 availability zones?**

No, a subnet can only exist within a single availability zone.


**How can I access AWS services if I have no Internet access?**

To access AWS services (i.e. S3) privately, you can use a VPC endpoint in your VPC. The VPC endpoint configuration will depend on the type of endpoint : Interface or Gateway.

**What is Route53?**

Route53 is the DNS service of AWS. One way to remember it is to remember that DNS runs on port 53, which is inlcuded in the name.

**What AWS services can I use to create a hybrid environment between my datacentre and AWS?**

You can use AWS VPN and AWS DirectConnect to create a connection between the 2 sites, depending on your requirements.