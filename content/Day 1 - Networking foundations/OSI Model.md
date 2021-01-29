---
title: "OSI Model"
draft: false
weight: 30
pre: 
---

All networking concepts are based on the OSI model:

<img src='/images/osi-model-7-layers.png' width='200px'>

Each layer has a meaning in networking. We will not cover the layers in dept, but you can read more about in the [Further Reading](/further_reading.html) section.

Networking is based on the OSI model, it is a bit like the layers of a cake, often referred as L1, L2, L3, etc..

Let's pick some real life examples:

- L1 = your home router, your cables

- L2 = your home devices interconnecting (find example)

- L3 = your home laptop/phone getting to the Internet

- L4 = when you stream an online movie

- L5 = when you download a file

- L6 = when you used Putty to login to your EC2 instance during Linux CloudOps workshop

- L7 = a website


(TO SPEECH)

L1 corresponds to anything physical, such as a device or a cable. If we go back to our chat about routers and switches, the devices as such will sit in L1 since they are physical.

However, although they're physical machines, they provide functionalities corresponding to other layers. A switch does not do any routing, meaning it does not know what is an IP address, and only work out connectivity inside a LAN. So a switch, in it is logical way, will sit in L2 Data layer.

On the other hand, a router allows routing and communication between different networks via IP adressing, so it works at the L3 Network layer.

L4 corresponds to anything (protocols or devices) related to transport of data across the network. 
(Can be firewall against L4 attacks, or examples of UDP streaming or TCP).

When we talk about API or establishing an end to end path to send data, we refer to L5 Session layer.

L6 Presentation layer for example SSH to login to instance, or SSL whe we check this small lock near the HTTP of the website we're on.

To finish, L7 is the website, the DNS protocol to resolve the webiste, etc.









