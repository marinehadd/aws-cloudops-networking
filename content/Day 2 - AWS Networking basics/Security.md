---
title: "Security in a VPC"
draft: false
weight: 40
pre: 
---


ACLs and SGs.

A **security group** is a virtual stateful firewall that controls inbound and outbound network traffic to AWS resources and Amazon EC2 instances. At AWS, security groups act like a built-in firewall for your virtual servers. With these security groups, you have full control about how accessible your instances are.
At the most basic level, it is just another method to filter traffic to your instances. It provides you control about what traffic to allow or deny. To determine who has access to your instances, you configure a security group rule. Rules can vary from keeping the instance completely private, completely public, or somewhere in between.

A **Network access control list** (network ACL) is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets

<img src='../images/sg_nacl.png' width='600px'>










