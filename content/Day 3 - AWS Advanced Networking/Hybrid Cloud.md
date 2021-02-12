---
title: "Hybrid Connectivity"
draft: false
weight: 55
pre: 
---


AWS allows you to integrate your on-premise network with your cloud environment, either:
- by using a Direct Connect connection (DX)
- by using a Virtual Private Network (VPN)

They can both be used for this purpose but are chosen based on different needs.

A VPN is an encrypted tunnel going over the Internet. There are two types of VPN in AWS:
- **Site-to-Site VPN** : this one is used between different sites, such as an on-premise network and the cloud, and uses IPsec type of VPN.

<img src='/images/sitetositevpn.png'>

- **Client VPN** : this one allows single clients to connect to specific resources.

<img src='/images/clientvpn.png'>

- Alternatively, if you require different features or use case, you can setup your own VPN instance with a Third Party Software.

**AWS Direct Connect** allows you to establish a direct connection from on-premise to AWS through a dedicated link.

There are several ways to use Direct Connect:
- There are several Direct Connect locations around the world to which you can connect your on-premise routers.
- You can work with an AWS Partner or a network provider to establish the connection from your on-premise data center to the AWS cloud.
- You can work with an AWS Partner to get a hosted connection, in which case you only get a slice of an existing Direct Connect link.

<img src='/images/dx.png'>

When connecting to AWS with Direct Connect, you need to setup a virtual interface to connect to the resources. When connecting to your private resources such as your VPCs, a private virtual interface will be required. When connecting to AWS services, a public virtual inerface will be required since they are considered as public services.

<img src='/images/dxpublic.png'>

In order to use the same existing Direct Connect link to connect to another region, you can use a Direct Connect Gateway. In this case, an interface is created from your existing Direct Connect endpoint to connect to the Gateway, and then the Gateway can connect to the different VPCs in the different regions.

<img src='/images/dx-gateway.png'>


*VPN VS. DX*

Feature | VPN | DirectConnect
--- | --- | ---
Encryption | YES | NO
Connection Type | VPN goes through the Internet | DX is a dedicated connection
Bandwidth | Limited to 1.25 GBPS | Between 1GBPS and 10GBPS
Costs | Cheaper | More expensive than VPN
Routing | Static/Dynamic | Dynamic only






