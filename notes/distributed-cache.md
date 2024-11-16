- [Caching](#caching)
- [Distributed Cache](#distributed-cache)
- [Challenges with Local Caching in Distributed Systems](#challenges-with-local-caching-in-distributed-systems)
- [Benefits of Distributed Cache](#benefits-of-distributed-cache)
  - [Example of the benefits of distributed caching](#example-of-the-benefits-of-distributed-caching)
- [Key Components of Distributed Caching](#key-components-of-distributed-caching)
  - [Cache Servers and their Roles](#cache-servers-and-their-roles)
  - [Data Partitioning and Replication Strategies](#data-partitioning-and-replication-strategies)
    - [Data Partitioning](#data-partitioning)
    - [Replication](#replication)
  - [Example of Data Partitioning and Replication](#example-of-data-partitioning-and-replication)
- [Popular Distributed Caching Solutions](#popular-distributed-caching-solutions)
- [Implementing Distributed Caching](#implementing-distributed-caching)
  - [Steps to setting up Distributed Cache](#steps-to-setting-up-distributed-cache)
  - [Best Practices for Cache Management](#best-practices-for-cache-management)
  - [Example of Distributed Cache Implementation](#example-of-distributed-cache-implementation)
- [Conclusion: Significance of Distributed Caching](#conclusion-significance-of-distributed-caching)
  - [Recap of the Importance of Distributed Caching](#recap-of-the-importance-of-distributed-caching)
  - [Key Takeaways](#key-takeaways)
- _Refs_: [Link 1](https://redis.io/glossary/distributed-caching/)

# Caching

- Caching is a technique for storing and retrieving frequently accessed data or computations to speed up subsequent requests, reducing time and resources needed to fetch data from the original source.
- Caching improves performance and reduces latency by temporarily storing data in a cache.
- Types of Caching: (i) Local Caching, (ii) Distributed Caching
- Local Caching
  - Involves storing data on a single machine or within a single application.
  - Best suited for scenarios with limited data retrieval needs or smaller data volumes.
  - E.g., browser caches and application-level caches.

# Distributed Cache

![Distributed Cache](./diagrams/distributed-cache-2.png)

- A distributed cache is a caching system that spreads data across multiple nodes in a cluster and across various data centers worldwide.
- Pools the RAM of multiple networked computers into a single in-memory data store, allowing for fast data access.
- Overcomes the memory limits of a single server by linking multiple computers, enabling growth and increased processing power.
- Particularly beneficial in environments with high data volume and load.
- Improves application reliability and speed by storing frequently accessed data closer to users, reducing latency.
- Decreases strain on backend systems by minimizing the need for frequent data retrieval from slower storage solutions.

# Challenges with Local Caching in Distributed Systems

- **Data Inconsistency**: Updated to local cache on one server are not propagated to others, leading to outdated data being served.
- **Increased Latency**: Relying on local caches across multiple servers can cause delays in ensuring data consistency.
- **Scalability Bottlenecks**: Local caching struggles to handle the demands of users accessing data from various locations.

# Benefits of Distributed Cache

- **Scalability**: Supports adding cache servers to handle growing application traffic without disrupting operations.
- **Fault Tolerance**: Ensures continuous availability of cached data by rerouting requests in case of server failures.
- **Performance**: Stores data closer to users, reducing fetch times and improving response times.

## Example of the benefits of distributed caching

Imagine a global online retailer with customers accessing its platform from multiple continents. If the retailer uses local caching, a user in Asia might experience slower response times when accessing data stored in a server in North America. With distributed caching, the retailer can store frequently accessed data in cache servers located in Asia, North America and other regions. As a result, users receive data from the nearest cache server, ensuring a consistent and fast browsing experience regardless of their location.

# Key Components of Distributed Caching

## Cache Servers and their Roles

- **Cache Servers**: Core components that store temporary data across multiple nodes for quick access.
- **Independent Operation**: Each cache server functions independently, contributing to system resilience.
- **High Availability**: Requests can be rerouted to another server in case of a cache server failure.
- **Fault Tolerance**: The system ensures continued operation despite server outages.

## Data Partitioning and Replication Strategies

---

### Data Partitioning

- Consistent Hashing
  - Distributes data evenly across cache servers.
  - Minimizes data movement during server additions/removals
- Virtual Nodes
  - Balances data distribution when cache servers have varying capacities.
  - Ensures that data distribution remains balanced even if some servers have higher storage capacities than others.

---

### Replication

- Ensures Data Availability
  - Maintains data accessibility during server failures
- Common Strategies:
  - **Master-Slave Replication**
    - One server is the master; others are replicas.
  - **Peer-to-Peer Replication**
    - Each server acts as both a primary store and a replica for distributed data.

---

## Example of Data Partitioning and Replication

Consider a social media platform that uses distributed caching to store user profiles. Using consistent hashing, the platform ensures that user profiles are evenly distributed across multiple cache servers. If a user from Europe accesses their profile, the system retrieves the data from a cache server located in Europe, ensuring low latency. To ensure data availability, the platform replicates each user profile on two or more cache servers. So, if one server fails, the system can still retrieve the user's profile from a replica server, ensuring uninterrupted service.

# Popular Distributed Caching Solutions

- **Redis**
  - Open-source, in-memory data store
  - Supports multiple data types (e.g., strings, lists)
  - High performance, scalability and persistence
- **Memcached**
  - Simple key-value store for speeding up web apps
  - Reduces database load with high connection support
- **Hazelcast**
  - In-memory data grid with caching, messaging and computing
  - Designed for cloud-native applications
- **Apache Ignite**
  - In-memory platform for caching, processing and transactions.
  - Supports data replication and querying

# Implementing Distributed Caching

## Steps to setting up Distributed Cache

1. Select a suitable distributed caching solution based on application requirements and infrastructure.
1. Install and configure the caching software on each node or server in the distributed system.
1. Define data partitioning and replication strategies to ensure efficient data distribution and high availability.
1. Integrate the caching solution with the application, ensuring that data reads and writes are directed to the cache.
1. Monitor and fine-tune the cache performance, adjusting configurations as needed for optimal results.

## Best Practices for Cache Management

- **Cache Eviction**: Implement appropriate cache eviction policies, such as Least Recently Used (LRU) or Time to Live (TTL), to ensure that the cache remains updated and relevant.
- **Data Consistency**: Ensure that the cache remains consistent with the primary data source, especially in scenarios where data is frequently updated.
- **Monitoring**: Regularly monitor cache hit and miss rates to understand cache effectiveness and make necessary adjustments.
- **Scalability**: Design the cache infrastructure to be scalable, allowing for easy addition of new cache nodes as the application grows.

## Example of Distributed Cache Implementation

Imagine an online streaming platform that experiences high traffic during new movie releases. To handle the increased load and ensure smooth streaming for users, the platform decides to implement a distributed cache. They choose Redis as their caching solution and set it up across multiple servers located in different regions. By partitioning movie metadata (different languages across regions) and frequently accessed content across these cache servers, the platform ensures that users can quickly access data from the nearest cache server. They implement a TTL-based eviction policy to refresh movie listings and monitor cache performance to ensure high hit rates. As a result, users experience faster streaming speeds, and the platform efficiently handles peak traffic loads.

# Conclusion: Significance of Distributed Caching

## Recap of the Importance of Distributed Caching

- **Purpose**: Improve performance, scalability, and real-time data access by caching frequently accessed data.
- Benefits
  - Reduces load on primary data sources
  - Ensures fast data retrieval
  - Enhances user experience by minimizing latency

## Key Takeaways

- Distributed caching addresses the limitations of local caching, especially in large-scale and geographically distributed applications.
- Several distributed caching solutions, each with its unique features and advantages, cater to different application needs.
- Effective cache management, including eviction policies and handling cache misses, is crucial for maximizing the benefits of caching.
