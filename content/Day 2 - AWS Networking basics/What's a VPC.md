---
title: "What is a VPC?"
draft: false
weight: 30
pre: 
---

**Amazon Virtual Private Cloud (Amazon VPC)** allows you to provision resources, such as Amazon EC2 instances, into a virtual network. This virtual network is a logically isolated area within the AWS cloud that resembles a traditional network. Think about it as a private data center in the cloud.

The VPC is highly available as it spans all of the Availability Zones in the Region where you launch it. When you create a VPC, you provide a CIDR block that specifies the range of IP addresses for the VPC. For example, _10.0.0.0/16_.

<img src='/images/vpc-diagram.png'>

A VPC can contain multiple **subnets** where you can launch AWS resources. Each subnet will reside in one Availability Zone and you can have multiple subnets in the same Availability zone. 

You must specify a CIDR block for the subnets from the range of your VPC. For example, _10.0.0.0/24_ and _10.0.1.0/24_. If you launch an EC2 instance inside the first subnet, it will have an IP address inside the _10.0.0.0/24_ range (for example, _10.0.0.42_). 

The VPC has an implicit router that uses **route tables** to direct traffic. Each subnet is associated with a route table that controls the routing for that particular subnet. If you don't associate explicitly a subnet with a particular route table, it will be implicitly associated the main route table:

Destination | Target
--- | ---
10.0.0.0/16 | local

Multiple subnets can be associated with the same route table. However, you can only associate a subnet with one route table.