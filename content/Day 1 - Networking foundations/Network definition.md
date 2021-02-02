---
title: "What is a network?"
draft: false
weight: 20
---

A network can be defined as a group of devices interconnected together via an edge networking component forming a dedicated and private environment.

Let's take an example:

<img src='/images/home_network.png' width='400px'>

There are several types of networks but the most common are LAN (Local Area Network) and WAN (Wide Area Network). As the names indicate, a LAN is defined by a single network (i.e. your house network) while a WAN allows interconnection between different LANs.

<img src='/images/LANWAN.png' width='400px'>


The main devices used in networking are switch and router. They work at different layers and allow connectivity inside and outside a network, respectively. 

The switch allows all devices in the network/LAN to communicate while the router sits on the edge of the LAN in order to provide external connectivity, either to the Internet or to another network/LAN.

So, a switch will allow intra-LAN connectivity, a router will allow inter-LAN connectivity.

A router is attached to a network via a network interface with a static IP address that belongs to that network. It can have different interfaces with different IP addresses, therefore belonging to different networks at the same time. In that case, the router doesn't need to communicate with another router to reach another network, the routing is done internally.

<img src='/images/routertypes.png' width='400px'>


The router IP address is called a Gateway IP, meaning it is the door via which all traffic is going, when a network host is trying to reach an external IP/host.

In real life, there are also devices that combine switch and router together, therefore can ensure both types of communication.

In a WAN, edge routers of the different LANs (refer to Example 2 above) route traffic to each other to allow communication between the different networks. 

<img src='/images/switch-and-router.png' width='400px'>


Now that we have the big picture, let's talk about networking layers.


