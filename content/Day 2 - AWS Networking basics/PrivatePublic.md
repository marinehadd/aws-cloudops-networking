---
title: "Private/Public concepts"
draft: false
weight: 35
pre: 
---

Resources launched inside a VPC will take an IP address from the CIDR block assigned. For example, for a _10.0.0.0/16_ CIDR block, an EC2 instance could have _10.0.0.42_ as its IP address. 

This IP address is private: it only makes sense inside the VPC and can't be reached from the Internet. In order to make the EC2 instance publicly reachable, two conditions must be fulfilled: the EC2 instance must have a public IP address and an **Internet Gateway** attached to the VPC.

An Internet Gateway is a highly available component that brings connectivity to your VPC, allowing access to the Internet. Your public resources must reside in a subnet that's associated with a route table that has a route to an Internet Gateway. This subnet is a **public subnet**. 

<img src='/images/nat-gateway-diagram.png'>

A **private subnet**, on the other hand, is associated with a route table that does not have a route to an Internet Gateway. The resources that should not be publicly accessible reside in these subnets. However, if your private resources need access to the Internet or other AWS services, you can add a **NAT Gateway**.

The NAT Gateway allow your EC2 instance to connect to the Internet, but prevent the Internet from connecting to it. The NAT Gateway resides in a public subnet in a certain Availability Zone. In order to allow your private subnets use the NAT Gateway to connect to the Internet, you must update the route tables they are associated with.

