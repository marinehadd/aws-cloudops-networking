---
title: "VPC Peering"
draft: false
weight: 60
pre:
---

A company may have multiple VPCs. For example, there could be a VPC for the finance department and another VPC for the legal department. The finance department may want to access resources in the legal department, and vice versa. In that case, yu will need a **VPC peering connection**.

A **VPC peering connection** is a networking connection between two VPCs that allows you to route traffic between them. Instances from one VPC can communicate with instances from the other VPC as if they are within the same network.

<img src='/images/peering-intro-diagram.png'>

You can have multiple VPC peering connections for each VPC. However, you can't establish **transitive peering relationships**. The following diagram illustrates it. VPC A has two peering connections with both VPC B and VPC C. VPC B and VPC C can't have a peering relationship through VPC A. They should establish a direct VPC peering connection between them in order to do so.

<img src='/images/transitive-peering-diagram.png'>















