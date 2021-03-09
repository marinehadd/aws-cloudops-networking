Create 2 VPCs and Setup VPC peering between VPCs.
Launch EC2 instances in each VPC and setup private connectivity between 2 instances.

<img src='../images/peering.png' width='600px'>

**Create a VPC 1:**
- Login to your AWS account
- Go to VPC Services and on the left panel, click on *Your VPCs*
- Click on *Create VPC* and give it a name (i.e. VPC-1) and a /16 CIDR block (i.e. 10.100.0.0/16), then leave the rest as default and click *Create VPC*
- Go back to the *Your VPCs* tab and check that your VPC has been created

**Create a public subnet 1:**

- Go to VPC Services and on the left panel, click on *Subnets*
- Click on *Create Subnet*
    + choose your VPC from the list
    + give it a name (PublicSub-1)
    + choose one of the Availability Zones
    + Use the first /24 of your VPC CIDR (i.e. 10.100.0.0/24)
    + Click *Create Subnet*

Now, your subnet is setup but can only communicate within the VPC by default.

**Create a private subnet 1:**

- Go to VPC Services and on the left panel, click on *Subnets*
- Click on *Create Subnet*
    + choose your VPC from the list
    + give it a name (PrivateSub1-1)
    + choose one of the Availability Zones
    + Use the first /24 of your VPC CIDR (i.e. 10.100.1.0/24)
    + Click *Create Subnet*

Now, your subnet is setup but can only communicate within the VPC by default.

**Create a public route table:**

- In the VPC Services tab, click on *Route Tables*
- Click on *Create Route Table*
    + choose your VPC from the list
    + give it a name (PublicRT-1)
    + Click *Create*
- On the Route Tables interface, look for your route table:
    + select the route table
    + on the panel at the bottom, click on *Subnet Associations*
    + *Edit subnet associations* and select your public subnet 1 and *Save*

Now, you have a public route table that will be used to route all external (such as Internet) traffic to and from your public subnet. However, we still don't know how to go to the Internet as we have no exit door yet.

**Create a IG 1:**

- In the VPC Services tab, click on *Internet Gateways*
- Click on *Create Internet Gateway*
    + give it a name (IGW-1) and *Create*
- Once it is created, you should be on its configuration page:
    + click *Actions* and select *Attach to VPC*
    + select your VPC 1 and *Attach*

Now, your Internet Gateway belongs to your VPC environment, so we can set it up to route all Internet traffic.

- In the VPC Services tab, click on *Route Tables*
- On the Route Tables interface, look for your public route table:
    + select the public route table
    + on the panel at the bottom, click on *Routes* then *Edit routes*
    + Click *Add route*, set the following:
        * Destination: 0.0.0.0/0   (0/0 means everywhere, it is not restricted to a specific network)
        * Target: Select Internet Gateway 1 from the drop-down and click on your IGW-XXXX
    + Save the changes

**Create a private route table:**

- In the VPC Services tab, click on *Route Tables*
- Click on *Create Route Table*
    + choose your VPC from the list
    + give it a name (PrivateRT-1)
    + Click *Create*
- On the Route Tables interface, look for your route table:
    + select the route table
    + on the panel at the bottom, click on *Subnet Associations*
    + *Edit subnet associations* and select your private subnet 1 and *Save*

**Create a private instance 1:**

- Go to EC2 Services and click on *Launch Instance*
    + select the 1st Amazon Linux AMI from the list
    + leave the Instance type as default and click *Next*
    + Set the below:
        * Network: choose your VPC 1
        * Subnet: choose your private subnet 1
        * Auto-assign Public IP: Select *Disable*
        * Leave the rest as default and go to the next page
    + Leave Storage as default and go to the next page
    + In Tags, create a tag with *Key* : Name and *Value* : PrivateEC2-1"
    + In the security group name the sg as *SG-Private-1* and change the source to 10.100.0.0/24. As we only want to ssh to it from our public instances in our public subnet.
    + In the Review and Launch page, click *Launch* and select your KP that you created and stored locally during the Linux course

**Create a public instance 1:**

- Go to EC2 Services and click on *Launch Instance*
    + select the 1st Amazon Linux AMI from the list
    + leave the Instance type as default and click *Next*
    + Set the below:
        * Network: choose your VPC 1
        * Subnet: choose your public subnet 1
        * Auto-assign Public IP: Select *Enable*
        * Leave the rest as default and go to the next page
    + Leave Storage as default and go to the next page
    + In Tags, create a tag with *Key* : Name and *Value* : PublicEC2-1"
    + In the security groups change the source to MyIP
    + In the Review and Launch page, click *Launch* and select your KP that you created and stored locally during the Linux course


Now, you have to copy those steps to create the same environment in the second VPC.



**Create a second VPC:**
- Login to your AWS account
- Go to VPC Services and on the left panel, click on *Your VPCs*
- Click on *Create VPC* and give it a name (i.e. VPC-"2") and a /16 CIDR block (i.e. 10.200.0.0/16), then leave the rest as default and click *Create VPC*
- Go back to the *Your VPCs* tab and check that your VPC has been created

**Create a second private subnet:**

- Go to VPC Services and on the left panel, click on *Subnets*
- Click on *Create Subnet*
    + choose your VPC from the list
    + give it a name (PublicSub-2)
    + choose one of the Availability Zones
    + Use the first /24 of your VPC CIDR (i.e. 10.200.1.0/24)
    + Click *Create Subnet*

**Create a private route table:**

- In the VPC Services tab, click on *Route Tables*
- Click on *Create Route Table*
    + choose your VPC from the list
    + give it a name (PrivateRT-2)
    + Click *Create*
- On the Route Tables interface, look for your route table:
    + select the route table
    + on the panel at the bottom, click on *Subnet Associations*
    + *Edit subnet associations* and select your private subnet 2 and *Save*

**Create a private instance 2:**

- Go to EC2 Services and click on *Launch Instance*
    + select the 1st Amazon Linux AMI from the list
    + leave the Instance type as default and click *Next*
    + Set the below:
        * Network: choose your VPC 2
        * Subnet: choose your private subnet 2
        * Auto-assign Public IP: Select *Disable*
        * Leave the rest as default and go to the next page
    + Leave Storage as default and go to the next page
    + In Tags, create a tag with *Key* : Name and *Value* : PrivateEC2-2"
    + In the security group part add one port for ssh and another for ping. The security group from our second VPC should allow instances in th private subnet of VPC 1 to ssh and ping from it.
    + Change source in the SSH type of the connection to *10.100.1.0/24* and add another route for *ALL ICMP IPv4*, set the source to *10.100.1.0/24*.
    + In the Review and Launch page, click *Launch* and select your KP that you created and stored locally during the Linux course

**Create a peering connection:**

- Open the Amazon VPC console at https://console.aws.amazon.com/vpc/.
 + In the navigation pane, choose Peering Connections, Create Peering Connection.
 + Configure the following information, and choose Create Peering Connection when you are done:
 + Peering connection name tag: You can optionally name your VPC peering connection.
 + VPC (Requester): Select the VPC in your account with which you want to create the VPC peering connection -> *10.100.0.0/16*
 + Under Select another VPC to peer with: Ensure My account is selected, and select another of your VPCs -> *10.200.0.0/16*
 + In the confirmation dialog box, choose OK.
 + Select the VPC peering connection that you've created, and choose Actions, Accept Request.
 + In the confirmation dialog, choose Yes, Accept. A second confirmation dialog displays; choose Modify my route tables now to go directly to the route tables page, or choose Close to do this later.

Note
If you cannot see the pending VPC peering connection, check the region. An inter-region peering request must be accepted in the region of the accepter VPC.
In the confirmation dialog box, choose Yes, Accept. A second confirmation dialog displays; choose Modify my route tables now to go directly to the route tables page, or choose Close to do this later.

Now we have to update the route tables to express the peering connection.

Add a Route in Private subnet of VPC 1 to connect to Private subnet in the VPC 2.

- In the VPC Services tab, click on *Route Tables*. Select the Route Table that is associated with the private subnet of the VPC 1.
+ on the panel at the bottom, click on *Routes* then *Edit routes*
    + Click *Add route*, set the following:
        * Destination: 10.200.1.0/24
        * Target: pcx-xxxxxxxx (select the peering coonnection you have just established)
    + Save the changes

Now you'll have to do the same for the second VPC.

Select the Route Table that is associated with the private subnet of the VPC 2.
+ on the panel at the bottom, click on *Routes* then *Edit routes*
    + Click *Add route*, set the following:
        * Destination: 10.100.1.0/24
        * Target: pcx-xxxxxxxx (select the peering coonnection you have just established)
    + Save the changes

Now the architecture is set up. You can try ssh to the instances and try to ping them.

**Test public connectivity to your public instance:**
- Open a terminal window, ssh in to the Ec2 instance in the Private subnet of the VPC 1.
- *ping* the private IP address of your instance  in the VPC 2 ( *ping X.X.X.X* )


Well done! Good job!