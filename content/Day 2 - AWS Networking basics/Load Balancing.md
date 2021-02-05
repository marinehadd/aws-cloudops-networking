---
title: "Elastic Load Balancing"
draft: false
weight: 45
pre: 
---



Explain goal of ELB and explain the 3 different types of ELBs and their main purpose/context.


**Elastic Load Balancing** automatically adjusts to incoming traffic and rapid changes in network traffic patterns by distributing traffic across multiple Amazon EC2 instances in the cloud, without manual intervention. This enables you to achieve higher levels of fault tolerance with your applications.

There are currently 3 types of a load balancer:


  •  Application Load Balancer
  
  
  •  Network Load Balancer
  
  
  •  Classic Load Balancer

<img src='../images/alb.png' width='600px'>


**Application Load Balancer** - Choose an Application Load Balancer when you need a flexible feature set for your web applications with HTTP and HTTPS traffic. Operating at the request level, Application Load Balancers provide advanced routing and visibility features targeted at application architectures, including microservices and containers.


**Network Load Balancer** - Choose a Network Load Balancer when you need ultra-high performance, TLS offloading at scale, centralized certificate deployment, support for UDP, and static IP addresses for your application. Operating at the connection level, Network Load Balancers are capable of handling millions of requests per second securely while maintaining ultra-low latencies.


**Classic Load Balancer** - Choose a Classic Load Balancer when you have an existing application running in the EC2-Classic network.






