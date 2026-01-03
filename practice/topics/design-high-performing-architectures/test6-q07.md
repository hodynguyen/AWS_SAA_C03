# Question 7

Spot EC2 fleet behind ALB. Need distributed session management with auto node failure detection, sub-millisecond latency, multithreaded.

Which is the best choice?

## Options

A. ElastiCache for Redis Global Datastore

B. ELB sticky sessions

C. ElastiCache for Memcached with Auto Discovery

D. RDS with RDS Proxy

## Correct Answer

**C. ElastiCache for Memcached with Auto Discovery**

## Explanation

Memcached with Auto Discovery:
- **Multithreaded**: Unlike Redis (single-threaded by default)
- **Auto Discovery**: Clients auto-detect all nodes
- **Node failure detection**: Automatic replacement
- **Sub-millisecond latency**: In-memory caching

### Why other options are incorrect:

- **A** - Redis is single-threaded; doesn't auto-detect failures.

- **B** - Sticky sessions tie users to servers; not scalable.

- **D** - RDS has higher latency than in-memory cache.

## References

- https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/AutoDiscovery.Benefits.html
- https://tutorialsdojo.com/amazon-elasticache/

## Domain

Design High-Performing Architectures
