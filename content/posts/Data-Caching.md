---
title: "What is a caching?"
date: 2023-03-17
description: "Breif intro to Data Caching"
tags: ["System Design", "software Architecture", "database"]
type: post
weight: 20
showTableOfContents: false
---
***
In computing, a cache refers to the technique of temporarily storing frequently accessed data in a fast-accessible storage layer, such as RAM, to reduce the response time and improve the overall system performance. Caching is widely used in various systems, including web applications, databases, operating systems, and more.

## Why Use Caching?
The main purpose of caching is to reduce the response time of the system. When a user requests data from the system, the system retrieves the data from the primary storage, which can be slow in some cases. However, if the system caches the frequently accessed data, it can quickly return the cached data to the user without accessing the primary storage. This can significantly reduce the response time and improve the user experience.

Another benefit of caching is that it can reduce the load on the primary storage. Since the frequently accessed data is already available in the cache, the system can avoid unnecessary read and write operations on the primary storage, which can improve the scalability and reliability of the system.

Let's take a look at this image:

![Figure](/images/caching/c-1.png "Preview")


From the image above, let's imagine a scenario where 6 Twitter users intend to access the same Twitter profile (which corresponds to the ID number one in the database). To make this possible, a GET request is sent to the backend when a user clicks on the profile. The backend then receives the request, processes it with the help of the database, and returns the result back to the user. While this method is functioning without any issues, it can become a major computing and performance burden when scaled up to handle a large number of requests. For instance, if 500,000 Twitter users wanted to view the same profile, the backend would have to process a corresponding number of GET requests, even though the profile remains unchanged.

To address this problem, caching can be used to store the profile associated with ID number one in the cache memory. By doing so, the backend can process requests using the cache instead of having to access the database each time, which significantly improves computing power and performance.

---

## Types of Caching

There are several types of caching techniques that can be used in system design, depending on the requirements and constraints of the system. The most common types of caching are:

### 1. Client-Side Caching

Client-side caching refers to the technique of caching data on the client-side, such as a web browser, mobile app, or desktop app. This technique is useful for reducing the network latency and improving the responsiveness of the application. However, client-side caching can also increase the memory usage and security risks, as the cached data can be accessed and manipulated by the client.

### 2. Server-Side Caching

Server-side caching refers to the technique of caching data on the server-side, such as in-memory cache or distributed cache. This technique is useful for reducing the database load and improving the scalability and performance of the system. However, server-side caching can also increase the complexity and maintenance cost of the system, as the cache needs to be synchronized and invalidated properly.

Some popular server-side caching technologies used today include:

- [Redis](https://redis.com): Redis is an in-memory data store that can be used as a cache, a database, or a message broker. It is designed for high performance and scalability, as it stores data in memory, which is much faster than disk-based storage. It also supports replication, clustering, and persistence, which makes it suitable for use in distributed systems and high-availability environments.

- [Memcached](https://memcached.org): Memcached is a distributed memory caching system that can be used to cache data across multiple servers. It provides fast read and write operations, as well as a simple key-value data model. It is also commonly used for caching session data, database query results, and API responses.
---
## Best Practices of Caching

To effectively use server-side or client-side caching, you need to identify the frequently accessed data that can benefit the most from data caching. This can easily be done by analyzing the system logs, monitoring the database queries, or profiling the application. Once the hot data is identified, it can be cached in the appropriate layer.

> Data coming from a GET request can be identified as _Hot Data_, since databases typically execute a large number of read operations compared to write operations.
  
---
## What is the catch?
Similar to any other tech solution, caching does have its drawbacks along with the benefits it brings to the table.

### 1. Cache Invalidation

One of the biggest challenges of caching is cache invalidation. When the database (all the records & tables) is updated, the cached data may become outdated. In such cases, the cache needs to be invalidated or refreshed to ensure that the users get the latest data. However, cache invalidation can be complex and expensive, especially in distributed systems or high-traffic applications.

### 2. Cache Overhead

Caching can also introduce overhead in terms of memory usage, CPU cycles, and network bandwidth as cached-data is stored in RAM. When the cache is full, it needs to evict some data to make space for new data. This process can be time-consuming and may affect the overall system performance. Moreover, cache coherence and synchronization can also consume resources and add complexity to the system.
  
### 3. Cache Consistency

Maintaining cache consistency can be another challenge in distributed systems or multi-tier architectures. When the same data is cached in multiple locations, it needs to be synchronized and consistent across all the caches to avoid data inconsistencies or race conditions. This can be especially challenging in dynamic or high-availability environments where the topology and state of the system can change frequently.

### 4. Cache Security

Caching can also introduce security risks, as the cached data can be accessed or manipulated by unauthorized users. For example, a malicious user can inject fake data or steal sensitive data from the cache. Therefore, it is essential to implement proper security measures, such as data encryption, access control, and data validation, to protect the cache from security threats.

---
## Conclusion

Caching is a powerful technique for improving system performance and reducing database load. However, it is important to understand the potential drawbacks and trade-offs of caching and choose the appropriate caching strategy based on the requirements and constraints of the system. By following best practices and using reliable caching technologies, such as Redis or Memcached you can effectively leverage caching to deliver fast, scalable, and reliable systems.