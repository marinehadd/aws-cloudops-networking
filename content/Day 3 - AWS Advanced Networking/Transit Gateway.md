---
title: "Transit Gateway"
draft: false
weight: 70
pre: 
---

VPC peering connections can become complicated when there are too many VPCs trying to communicate, the configuration and management becomes heavy (without also forgetting the VPC peering number limits).
In which case, a good practice is to use a **Transit Gateway** to establish connectivity between the VPCs.

<img src='/images/tgw.png'>


A Transit Gateway acts like a central router to centralize routing across the different networks such as VPCs and on-premise networks. This component works with VPCs, VPNs and Direct Connect connections. The routing decisions are based on route tables attached to each component at the Transit Gateway.

The key terms:
- Attachement
- Attachment route table
- Routes
    + static
    + propagation
    + blackhole

The Transit Gateway route tables work out the way to route traffic, however local network route tables are still required to direct the local traffic to the Transit Gateway for specific destination (like for a router to direct traffic to another router).

<img src='/images/tgwroutetable.png'>


Having such routing allows customers to manage their routing centrally but also to centralize other services such as Internet (i.e. picture above), security services, etc.

It also becomes convenient when 2 environments living in different regions need to be able to communicate, Transit Gateways can be peered.


<img src='/images/tgwpeering.png'>
