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

The VPC has an implicit router that uses **route tables** to direct traffic. Each subnet is associated with a route table that controls the routing for that particular subnet. If you don't associate explicitly a subnet with a particular route table, it will be implicitly associated with the main route table:

Destination | Target
--- | ---
10.0.0.0/16 | local

Multiple subnets can be associated with the same route table. However, you can only associate a subnet with one route table, except for the default (or main) route table that is automatically generated at the VPC creation.

As we discussed in Traditional Networking, the first IP and the last IP of a CIDR are reserved for Network ID and Broadcast respectively.
AWS reserves 5 IPs by default within each subnet:
- the first IP : Network ID
- the second IP : VPC router (referred as the router gateway in traditional networking)
- the third IP : DNS resolver
- the fourth IP : reserved for future use
- the last IP : broadcast address

So, if our subnet is 10.10.1.0/24, the following IPs will be reserved:
- 10.10.0.0
- 10.10.1.1
- 10.10.1.2
- 10.10.1.3
- 10.10.1.255

In AWS, the maximum size of a CIDR is /16 and the minimum size is /28, which means:

<p>/28 = 1111 1111.1111 1111.1111 1111.1111 0000 = 255.255.255.240<br>
255 - 240 = 15<br>
Because a network starts from .0 (.0 to .15), there are 16 addresses in a /28. However, we need to remove the 5 reserved IPs, therefore it gives us 11 IPs available for use. <br>
That means that if you need more than 11 IPs in your network, you will need to have a bigger CIDR such as /27 or above.</p>


<h4>LAB 1:</h4>

The final architecture of the Lab can be found in [Lab Architecture](/lab_diagram.html) section.

- Login to your AWS account
- Go to VPC Services and on the left panel, click on *Your VPCs*
- Click on *Create VPC* and give it a name (i.e. VPC-"Your Initials") and a /16 CIDR block (i.e. 10.10.0.0/16), then leave the rest as default and click *Create VPC*
- Go back to the *Your VPCs* tab and check that your VPC has been created

