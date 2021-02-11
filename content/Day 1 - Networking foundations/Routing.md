---
title: "Routing"
draft: false
weight: 45
pre: 
---

The router comes into the picture when different hosts from different networks try to communicate. We have seen in a previous section that the router does all the routing to allow the internal hosts to talk to an external destination such as the Internet or just another network.

This communication is done by the means of routing tables and routing protocols.

A route table is a source/destination map for the router to know where to send the traffic, based on the traffic destination.

*NB: ISP = Internet Service Provider*

<img src='/images/routetables.png' width='1000px'>

The source and destination correspond to subnets.

<img src='/images/routing.png' width='1000px'>

There are two types of routing:
- static routing : routes are manually added to route tables
- dynamic routing : routes are dynamically using routing protocols


There are several routing protocols, but the most commonly used are OSPF and BGP.

OSPF is used to dynamically route traffic between networks of a same domain, while BGP is used to dynamically route between networks of different OSPF domains for example.


<img src='/images/protocols.png' width='400px'>









