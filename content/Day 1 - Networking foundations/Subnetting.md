---
title: "Subnetting"
draft: false
weight: 40
pre: 
---


A network (or LAN) is defined by a a block of IP addresses called a CIDR block, from which every host in the network receives an IP address.

A CIDR indicates the size of a network, and networks are calculated with subnetting. 
Subnetting allows the segmentation of a bigger network in smaller networks. For example, a company could have different departments (HR, Finances, etc) and therefore wish to seggregate their corporate network based on these departments. So, each department will be allocated a portion of the big network (CIDR).

<img src='/images/segmentation.png' width='400px'>

**Anatomy of a an IP address:**

An IP address is made of 4 octets, 1 octet equals to 8 bits. So the maximum lenght of an IP address is 32 bits.

IP addresses are translated from binaries, so each number represents an octet and an octet ranges from 0 to 255.

<img src='/images/octet.png' width='500px'>

Example:

0000 0000 = 0
1111 1111 = 255

=> 1111 1111.1111 1111.1111 1111.1111 1111 = 255.255.255.255

**How is this calculated?**

Each bit is a power of 2 (X^2) and is calculated from right to left.

<img src='/images/subnettable.png' width='1200px'>

*Example:*

192.168.1.0 => 1100 0000.1010 1000.0000 0001.0000 0000

(Drawing examples)

**Subnet Masks**

An IP address is segmented in 2 parts : 
- The Network section (always the left part)
- The Host section (always on the right).

The Host section defines the number of IPs available in a network.
The Network section remains the same for all the hosts in a same network, ad is called the Network ID.

*Example:*

Network: 10.1.1.0/24
Host 1: 10.1.1.1
Host 2: 10.1.1.2
Host 3: 10.1.1.4


The /24 is called the subnet mask and determines which parts of the IP are the network portion and the host portion.

/24 represents 24 bits:

1111 1111.1111 1111.1111 1111.0000 0000 = 255.255.255.0

2552.255.255 = network section
0 = host section

Going back to the previous example:

10.1.1.0/24 = 10.1.1.0/255.255.255.0

So, the network ID is 10.1.1.0, and hosts can only be allocated in the .0 octet.

*Examples:*

192.168.0.0/16 = 192.168.0.0/255.255.0.0
Network ID = 192.168.0.0
Host range = 192.168.0.0 - 192.168.255.255

192.168.128.0/17 = 192.168.128.0/255.255.128.0
Network ID = 192.168.128.0
Host range = 192.168.128.0 - 192.168.255.255

The host range allows to calculate the number of hosts you can have in the network. The way to calculate is as follow: *2^(Nb of host bits)*.

(That will matter if you want to know which size of a network to choose if you need X IPs)

*Example:*

- 192.168.0.0/16 has 16 host bits so 2^16 = 65536 hosts
- 10.1.1.0/24 has 8 host bits so 2^8 = 256 hosts


So, the smaller the network portion is, the more hosts you can allocate. 

So, as we talked about segmenting big networks into smaller networks, we can divide big CIDR into small CIDR. 

*How to calculate?*

/16 = 16 bits = 2^16 65536 hosts
/24 = 8 bits = 2^8 = 256 hosts
=> 65536/256 = 256

So there are 256 /24 subnets in a /16 subnet.

/24 = 8 bits = 2^8 = 256 hosts
/25 = 7 bits = 2^7 = 128 hosts
=> 256/128 = 2

So there are 2 /25 subnets in a /24 subnet.




(Show IP address on ipconfig laptop - show IP allocated, network, router gateway IP.)











