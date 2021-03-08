---
title: "Elastic Load Balancing"
draft: false
weight: 45
pre: 
---

The main purpose of a load balancer is to balance the load of your traffic across several servers.

Load balancers in AWS are called elastic because they can dynamically adjust based on the load, and provide a lot more features than traditionally.

**Elastic Load Balancing** automatically adjusts to incoming traffic and network changes by distributing traffic across multiple Amazon EC2 instances in the cloud, without manual intervention. This enables you to achieve higher levels of fault tolerance with your applications.

There are currently 3 types of a load balancer:


  •  Application Load Balancer
  
  
  •  Network Load Balancer
  
  
  •  Classic Load Balancer

<img src='../images/elb.png' width='600px'>


**Application Load Balancer** - As it's name indicates, this type works at the application level (L7 in the OSI model) and also provides advanced routing and features. 
For instance, if you need to load balance web servers working on HTTP/HTTPS and want to make the most of advanced features then you should use the application load balancer.
When you setup an application load balancer, you are only provided with its DNS name, but no IP address.

**Network Load Balancer** - The network load balancer works at the transport level (L4 in the OSI model) and in most cases, is used when high performance is required. Let's say you know you'll get thousands of requests per second, then the network load balancer might be a good option.
One advantage, depending on the context, of a network load balancer is that it is provided a static IP address (that will not change).


**Classic Load Balancer** - A classic load balancer works both at L4 and L7 of the OSI model, but has limited features.






