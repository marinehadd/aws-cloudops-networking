---
title: "Subnetting"
draft: false
weight: 40
pre: 
---


A network (or LAN) is defined by a a block of IP addresses called a CIDR block, from which every machine in the network receives an IP address.

PICTURE

CIDR have the purpose of sizing and seggregating networks. If you have a small home network, you will only need a few IP adresses, therefore the CIDR should be small, but if you work in a company where plenty of devices need to connect, and therefore require an IP address, then the size needs to be bigger.

How is a CIDR calculated?

the full lenght of an IP address is 32 bits.

IP addresses are written in binaries and translated into numbers called octets, so each number representing 8 bits.

<img src='/images/octet.png' width='200px'>


This is segmented in 2 parts : the subnet ID (always the left part), and the network ID (always on the right).

The subnet mask defines the size of your network, the network part defines the number of IP addresses (called hosts) that you can use in your network.

A subnet is calculated from right to left, as below:

<img src='/images/subnettable.png' width='200px'>


255 is the maximum number you can have over an octet, therefore the subnet mask covers the full lenght, giving no space for IP address use. As a result, the subnet mask is /32, the maximum size in an IP address.



A few examples:




Show IP address on ipconfig laptop.

Tutorial: https://acloud.guru/overview/124ee946-2249-40c2-a664-aa26af523920?_ga=2.78699287.2097752874.1606729826-1802322676.1602598892










