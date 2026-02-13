# Amazon ElastiCache Overview

## 1. What is ElastiCache?
- It is a managed **In-memory Database** service.
- **Goal**: Extremely high performance (Microseconds latency), reduced load on main databases (RDS).
- **Engines**: Supports **Redis** and **Memcached**.

## 2. Redis vs. Memcached (The Classic Exam Question)

| Feature | **Redis** | **Memcached** |
| :--- | :--- | :--- |
| **Complexity** | High (Advanced data types: Lists, Sets, Sorted Sets) | Low (Simple Key-Value store) |
| **Multi-AZ** | **YES** (High Availability, Auto Failover) | **NO** (If a node dies, cache is lost) |
| **Persistence** | **YES** (Data saved to disk/AOF) | **NO** (Pure in-memory, loose data on reboot) |
| **Backup & Restore** | **YES** (Point-in-time recovery) | **NO** |
| **Scalability** | Scale Read (Read Replicas) & Scale Write (Sharding - Cluster Mode) | Scale Out (Add nodes) - Multi-threaded |
| **Use Case** | Complex Caching, Leaderboards, Pub/Sub, Geospatial, Session Store (Persistent) | Simple Object Caching, Multithreaded performance needed |

> **Rule of Thumb:** Use **Redis** for almost everything (HA, Backup, Features). Only use **Memcached** if you need a very simple, sharded cache model with multi-threading.

## 3. Caching Strategies

### A. Lazy Loading (Cache-Aside) - Best for Read-Heavy
1. App asks Cache: "Do you have data X?"
2. **Miss**: Cache says "No".
3. App asks DB: "Get data X".
4. App writes data X to Cache.
5. Next time, App asks Cache -> **Hit**.
- **Pros**: Only requested data is cached (efficient).
- **Cons**: First request is slow (Cache miss penalty). Stale data (if DB updates, Cache doesn't know).

### B. Write Through - Best for Write-Heavy / Consistency
1. App updates DB.
2. App immediately updates Cache.
- **Pros**: Data in Cache is always fresh.
- **Cons**: Write is slower (must write to 2 places). Cache is full of data that might never be read.

## 4. Session Store (Use Case)
- Used to store user login sessions (Cookies, JWTs) so users don't have to re-login if the web server restarts or scales.
- **Why Redis?** Because of TTL (Time to Live) feature - auto expire session after 30 mins.

## 5. Redis Use Cases (Gaming/Real-time)
- **Leaderboards (Redis Sorted Sets)**: Who is Top 1? The uniqueness and guaranteed order of Sorted Sets make this easy.
- **Pub/Sub**: Real-time chat messaging.
