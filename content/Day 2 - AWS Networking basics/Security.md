---
title: "Security in a VPC"
draft: false
weight: 40
pre: 
---


A **security group** is a virtual stateful firewall that controls inbound and outbound network traffic to AWS resources and Amazon EC2 instances. At AWS, security groups act like a built-in firewall for your virtual servers. With these security groups, you have full control about how accessible your instances are.
At the most basic level, it is just another method to filter traffic to your instances. It provides you control about what traffic to allow or deny. To determine who has access to your instances, you configure a security group rule. Rules can vary from keeping the instance completely private, completely public, or somewhere in between.
When you first configure a Security Group, all access is denied, so you need to add rules to allow traffic to flow. 
Security Groups are stateful, that means that anything that you allow to flow out of your instance is allowed by default to flow back in your instance. 

A **Network access control list** (network ACL) is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets.
When you first configure a Network ACL, all access is allowed by default.
NACL are stateless, that means that if you want to allow a type of traffic, you need to do it both for inbound and outbound.

<img src='../images/sg_nacl.png' width='600px'>


In summary, the Network ACL acts at the subnet level. The Security Groups acts at the instance level.


<h4>LAB 3:</h4>

Refer to [Lab Architecture](/lab_diagram.html) for architecture.

**Create a public instance:**

- Go to EC2 Services and click on *Launch Instance*
    + select the 1st Amazon Linux AMI from the list
    + leave the Instance type as default and click *Next*
    + Set the below:
        * Network: choose your VPC
        * Subnet: choose your public subnet
        * Auto-assign Public IP: Select *Enable*
        * Leave the rest as default and go to the next page
    + Leave Storage as default and go to the next page
    + In Tags, create a tag with *Key* : Name and *Value* : PublicEC2-"YourInitials"
    + Leave the security group as default
    + In the Review and Launch page, click *Launch* and select your KP that you created and stored locally during the Linux course

Let it spin up, and create your private instance in the meantime.

**Create a private instance:**

- Go to EC2 Services and click on *Launch Instance*
    + select the 1st Amazon Linux AMI from the list
    + leave the Instance type as default and click *Next*
    + Set the below:
        * Network: choose your VPC
        * Subnet: choose your private subnet
        * Auto-assign Public IP: Select *Disable*
        * Leave the rest as default and go to the next page
    + Leave Storage as default and go to the next page
    + In Tags, create a tag with *Key* : Name and *Value* : PrivateEC2-"YourInitials"
    + Leave the security group as default
    + In the Review and Launch page, click *Launch* and select your KP that you created and stored locally during the Linux course
    ***If you deleted your key pair, just create a new one and download it.***

Now you should have 1 public instance and 1 private instance. In the EC2 interface, if you select them one by one and look at the bottom panel, you should see all details about the instances.
Notice that your public EC2 has a public IPv4 address as well as a public DNS name, on the opposite of the private EC2 that only has private addresses.

**Edit the Security Group:**

- On the public EC2 bottom panel, select the Security tab. The only rule allowed is SSH on port 22 from anywhere (o.o.o.o/0). Even if we want this instance to be publicly reachable, we do not want everyone to SSH into it and change configuration.
- Click on the Security Group and *Edit Inbound rules*
    + set the *Source* as *My IP* and in parallel, verify that it matches your IP address by typing ***whatsmyip*** in another browser tab
    + Add a new rule with Type as *All ICMP - IPv4* and Source as your IP again
    + *Save rules*

Now that we have SSH and ICMP traffic allowed from our IP address, it means only you will be able to connect only on these specific ports to the instance.

SSH (port 22) is the protocol used to login to your instance's CLI.
ICMP (no port number) is the protocol used to communicate between instances at the network level. For example, we use the command *ping* to test connectivity from one instance to another, and this command uses ICMP protocol.

We will not be using NACL today as it is not required in this context, but you can have a look at the default one by going to VPC Services -> Subnets -> Network ACL (bottom panel).


**Test public connectivity to your public instance:**
- open a terminal window and *ping* the public IP address of your instance ( *ping X.X.X.X* )
- Try to login to your instance (refer to https://linuxworkshop.aws-cloudops.com/2.logging_in.html if you need the steps to use your key pair to login)

If you do the same test on the private IP address of this same instance (public instance), you will notice that all traffic is blocked.

We cannot do the same with the private instance since there is no public IP, you can try to SSH to its private IP to prove that it is not reachable.
A way to SSH into it would be to setup a Bastion instance. This instance is a public instance that just acts as a jump box in order to connect to private instances securely. Despite being public, this instance would also have a private IP address belonging to that same VPC, therefore routable to the private subnet of the private instance.


**Cleanup:**

You can keep this setup to work on different labs and/or play around with the AWS resources.

If not, don't forget to cleanup your setup by deleting resources in the reverse order of the lab steps.
