TODO:

- Rate Limiting algorithms (don't understand some)
- understand LB SSL (??? What's this)

- [Caching] Redundant Storage: Same data may be stored across multiple nodes, leading to extra storage use.
	- Don't really understand this part

- Example: A relational database like MySQL uses query caching to store the results of frequent queries, allowing repeated requests to return results quickly without re-executing the query.
	- How does it know when to re-execute the query when the results of the query has changed?

- For Smaller Systems, if a CDN is not feasible for smaller systems, consider the following approach:
Separate Subdomain: Serve static media from a different subdomain using a lightweight HTTP server (e.g., Nginx, Apache).
DNS Cutover: Transition the DNS from this subdomain to a CDN layer when scaling or demand increases.
	- Does this mean that the subdomain serves as a CDN for smaller systems? How does this work? Give an example to help me to understand this concept.

Disk Cache
Description: A cache that stores frequently accessed data from disk to reduce read times.
Details: Unlike CPU caches, disk caches are often managed by software, typically the operating system kernel.
Example: The page cache in main memory that keeps copies of frequently accessed disk pages to minimize disk I/O operations.
	- dont really understand how disk cache works

- still dont really understand distributed cache

- [distributed cache] data partitioning virtual nodes

Technology Integration
Amazon CloudFront: Used in conjunction with Amazon S3 for efficient content distribution.
	- How does this work well with CDN?

Does netflix use CDN to stream videos and movies?

How does AWS Cloudfront serve dynamic content? 

What is CloudFront functions? Is that edge logic computations? And what is the purpose?

What are AWS serverless compute features?

How does VPN work? Does it change your location?

What does "burst" in rate limiting algorithm mean?

Why is "fixed window counting" algorithm bad for traffic burst?

Do not really understand "sliding window log" algorithm...

Why is server side rate limiting more secure and easy to manage as compared to client side rate limiting?