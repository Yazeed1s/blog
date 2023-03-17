---
title: "What is a load balancer?"
date: 2023-01-13
description: "Breif intro to Load Balancers"
tags: ["System Design", "software Architecture"]
type: post
weight: 20
showTableOfContents: false
---
***
## what is a load balancer?

A load balancer is a component that acts as a reverse proxy and evenly distributes network or application traffic across multiple servers ensuring that no single server bears all the workload(see figure 1). The workload distribution between servers undoubtedly enhances the reliability, responsiveness, flexibility and availability of the system. 

![Figure](/images/Load-Blanacer/balancer1.png "Preview")
figure 1

For additional scalability and redundancy, we can try to load balance at each layer of our system:

![Figure](/images/Load-Blanacer/balancer2.png "Preview")

## Why load balancers?

The workload on a single server will increase as the business demand & number of users grows. One of the available solutions to handle this grow is to add more servers. Apparently, the workload needs to be distributed among the servers by a `load balancer` which in return helps the system to operate more efficiently.

Generally speaking, modern high-traffic websites serve hundreds of thousands, if not millions, of **concurrent** requests from users (think of amazon as an example). High-traffic systems need `N` number of servers & some sort of workload distribution in order to function effectively and efficiently. 

***

## Types of load balancers

A load balancer can be hardware-based or software based and it can operate at different levels of the network stack, including the application layer, transport layer, and network layer.

***

## How does a load balancer work?

A load balancer can sit in front of the servers and work by distributing network traffic across multiple servers in a manner that helps to ensure that no single server is overwhelmed, and to improve the overall reliability, responsiveness and availability of the applications. 

A general overview of how load balancers work:

1.  Client requests: When a client device makes a request to access an application or service, the request is sent to the load balancer.

2.  Traffic distribution: The load balancer uses a load balancing algorithm to determine which server should handle the request. The algorithm takes into consideration factors such as the current load on each server, the location of the client, and the type of request being made.

3.  Server selection: Once the load balancer has determined which server should handle the request, it forwards the request to that server.

4.  Server response: The selected server processes the request and returns a response back to the load balancer.

5.  Client response: The load balancer then forwards the server's response back to the client device.
 

In this way, the load balancer acts as an intermediary between the client and the servers, distributing traffic in a manner that helps to improve performance, reliability, and availability. The specific details of how a load balancer works can vary depending on the type of load balancer and the load balancing algorithm being used, but the general principles outlined above remain the same.

***

## Is it essential? 

Whether or not a load balancer is essential for a system depends highly on the specific needs and requirements of the system. However, in many cases, a load balancer can be a valuable component of a system, providing several key benefits, including improved reliability and availability, better performance, scalability, security, and easier maintenance.

If the system is expected to handle a large amount of traffic, a load balancer can definitely help distribute the traffic across multiple servers, improving performance and reducing the risk of server failure. Similarly, if the system is expected to grow over time, a load balancer can make it easier to add or remove servers as needed, making it easier to scale the infrastructure as demand dictates.

In short, while a load balancer may not be essential for every system, it can provide a number of valuable benefits that can help organizations to improve the performance, reliability, security, and scalability of their applications and services.

***

## Benefits of load balancers:

Load balancers provide several key benefits, including:

1. Improved reliability and availability: By distributing traffic across multiple servers, load balancers help to ensure that even if one server fails, the others can pick up the slack and continue to serve client requests. This helps to improve the overall reliability and availability of the applications and services being offered.

2.  Better performance: Load balancers can help to distribute traffic in a way that ensures that no single server is overworked, leading to improved performance and reduced response times.

3.  Scalability: Load balancers allow you to easily add or remove servers as needed, making it easier to scale the infrastructure up or down as demand dictates.

4.  Security: Load balancers can help to protect servers from malicious attacks by screening traffic and blocking malicious requests before they reach the servers.

5.  Easier maintenance: Load balancers allow performing maintenance and upgrades on individual servers without affecting the overall availability of your applications and services.

6.  Traffic management: Load balancers allow managing traffic based on a variety of criteria, such as geographical location, type of device, and URL, to ensure that users are directed to the appropriate server for their needs.
 
Overall, load balancers provide a number of benefits that can definitely help to improve the performance, reliability, security, and scalability of the application/services.

***

## Single point of failure!
As you must've already guessed, despite all the great benefits, a load balancer itself can be a single point of failure. To prevent this, a second or `N` number of load balancers can be used in a cluster mode. And, if there's a failure detection and the active load balancer fails, another load balancer can take over.

## Load balancing algorithms:
Now, let's discuss commonly used algorithms:

-   **Round-robin**: Requests are distributed to application servers in iterations.
-   **Weighted Round-robin**: Based on the simple Round-robin algorithm but it accounts for differing server characteristics such as compute and traffic handling capacity using weights that can be assigned via DNS records by the administrator.
-   **Least Connections**: A new request is sent to the server with the fewest current connections to clients. The relative computing capacity of each server is factored into determining which one has the least connections.
-   **Least Response Time**: Sends requests to the server selected by a formula that combines the fastest response time and fewest active connections.
-   **Least Bandwidth**: This method measures traffic in megabits per second (Mbps), sending client requests to the server with the least Mbps of traffic.
-   **Hashing**: Distributes requests based on a key we define, such as the client IP address or the request URL.
***
