---
title: "Subnetting"
draft: false
weight: 40
pre: 
---


A network (or LAN) is defined by a a block of IP addresses called a CIDR block, from which every host in the network receives an IP address.

A CIDR indicates the size of a network, and networks are calculated with subnetting. 
Subnetting allows the segmentation of a bigger network in smaller networks. For example, a company could have different departments (HR, Finances, etc) and therefore wish to segregate their corporate network based on these departments. So, each department will be allocated a portion of the big network (CIDR).

<img src='/images/segmentation.png' width='400px'>

<h3> Anatomy of a an IP address: </h3>

An IP address is made of 4 octets, 1 octet equals to 8 bits. So the maximum length of an IP address is 32 bits.

IP addresses are translated from binaries, so each number represents an octet and an octet ranges from 0 to 255.

<img src='/images/octet.png' width='500px'>

***Example:***

<p>0000 0000 = 0<br>
1111 1111 = 255</p>

=> 1111 1111.1111 1111.1111 1111.1111 1111 = 255.255.255.255

**How is this calculated?**

Each bit is a power of 2 (X^2) and is calculated from right to left.

<img src='/images/subnettable.png' width='1200px'>

***Example:***

192.168.1.0 => 1100 0000.1010 1000.0000 0001.0000 0000




<h3> Subnet Masks </h3>

An IP address is segmented in 2 parts : 
- The Network section (always the left part)
- The Host section (always on the right).

The Host portion defines the number of IPs available in a network.
The Network portion remains the same for all the hosts in a same network and is called the Network ID.
A subnet mask represents the number of bits (out of 32) used in the network portion.

***Example:***

<p>Network: 10.1.1.0/24<br>
Host 1: 10.1.1.1<br>
Host 2: 10.1.1.2<br>
Host 3: 10.1.1.4</p>




The /24 is the subnet mask and defines the size of the network portion, and therefore the number of bits left for the host portion (= number of available IPs to use in the network). 



/24 represents 24 bits:

<p>1111 1111.1111 1111.1111 1111.0000 0000 = 255.255.255.0<br>
255.255.255 = network section<br>
0 = host section</p>



Going back to the previous example:

10.1.1.0/24 = 10.1.1.0/255.255.255.0

So, the network ID is 10.1.1.0, and hosts can only be allocated in the .0 octet.



***Examples:***

*Example 1:*

<p>192.168.0.0/16 = 192.168.0.0/255.255.0.0<br>
Network ID = 192.168.0.0<br>
Host range = 192.168.0.0 - 192.168.255.255</p>

*Example 2 :*
<p>192.168.128.0/17 = 192.168.128.0/255.255.128.0<br>
Network ID = 192.168.128.0<br>
Host range = 192.168.128.0 - 192.168.255.255</p>


The host range allows to calculate the number of hosts you can have in the network. The way to calculate is as follow: *2^(Nb of host bits)*.


***Example:***

- 192.168.0.0/16 has 16 host bits so 2^16 = 65536 hosts
- 10.1.1.0/24 has 8 host bits so 2^8 = 256 hosts


So, the smaller the network portion is, the more hosts you can allocate. 

So, as we talked about segmenting big networks into smaller networks, we can divide big CIDR into small CIDR. 

**How to calculate?**

<p>/16 = 16 bits = 2^16 65536 hosts<br>
/24 = 8 bits = 2^8 = 256 hosts<br>
=> 65536/256 = 256</p>

So there are 256 /24 subnets in a /16 subnet.

<p>/24 = 8 bits = 2^8 = 256 hosts<br>
/25 = 7 bits = 2^7 = 128 hosts<br>
=> 256/128 = 2</p>

So there are 2 /25 subnets in a /24 subnet.

One last thing to remember is that there are always 2 IP addresses that cannot be used within a subnet:
- The first IP (10.1.1.0 if the subnet is 10.1.1.0/24) since it is reserved for the Network ID
- The last IP (10.1.1.255 if the subnet is 10.1.1.0/24) since it is reserved for the Broadcast IP. The broadcast IP is the IP used within a network to send messages to everyone in the network.

Not always but in most cases, as a best practice, the second IP of a subnet is dedicated to the router interface, called the Gateway IP. The gateway IP will be 10.1.1.1.1 if the subnet is 10.1.1.0/24.


***Exercise:***

- 10.20.3.2/24

<p>What is the binary address of 10.20.3.2?<br>
What is the network ID?<br>
What is the subnet mask?<br>
What is the gateway router IP address?<br>
How many IP addresses in this network?</p>










