---
title: "VPC Endpoints"
draft: false
weight: 75
pre: 
---



As we previsouly mentioned in the Direct Connect section, AWS services are considered "public" services unless they're setup in a VPC. This means that when an instance is trying to reach an AWS service (such as API Gateway, an S3 bucket, ..), the traffic is going out to the Internet because the service name resolves (DNS) to a public name/URL endpoint.

This situation therefore requires Internet access, therefore an Internet Gateway.

<img src='/images/publicservices.png'>


In some cases, you may not have any Internet access due to architecture requirements or compliance for example, in which case you cannot reach these AWS services.

A **VPC endpoint** is a component that allows resources to privately access AWS services, without going through the Internet. There are two types of endpoints: **Interface Endpoint** and **Gateway Endpoint**.

<h4> Gateway Endpoint </h4>

A Gateway endpoint can be configured for two services only: S3 and Dynamodb.

This type of endpoint is setup in the same way as you would setup any other route such as an Internet Gateway or a Transit Gateway. This is just an added route to the subnet route table to point any traffic destined for the service to the VPC endpoint.

<img src='/images/gatewayendpoint.png'>

An Interface endpoint can be configured for all services except Dynamodb.


<h4> Interface Endpoint </h4>

The way to connect to this endpoint is not via route table addition, but via an ENI (elastic network interface). When an Interface endpoint gets created, an ENI is automatically created for this endpoint in the same VPC. 

Therefore, because we have seen that all resources within a VPC can route to each other by default, then the Interface endpoint is made available to all resources within the VPC.


<img src='/images/interfaceendpoint.png'>




