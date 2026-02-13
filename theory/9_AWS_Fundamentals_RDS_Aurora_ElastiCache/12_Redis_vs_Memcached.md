# Redis vs Memcached - Deep Dive

## I. Redis (Remote Dictionary Server)

Redis is an advanced key-value store. It is often described as a **data structure server** because keys can contain strings, hashes, lists, sets, and sorted sets.

### 1. Architecture
- **Single-Threaded**: Redis uses a single-threaded event loop. This means requests are processed sequentially (one after another).
  - *Why is it fast?* Because it's purely in-memory (RAM) and avoids context-switching overhead. One thread can handle millions of requests per second.
  - *Limitation*: It can't utilize multiple CPU cores for a single shard. To scale CPU, you must use **Sharding (Cluster Mode)**.

### 2. Data Persistence (Độ bền dữ liệu)
Unlike Memcached, Redis can save data to disk:
- **RDB (Redis Database File)**: Snapshots data at specific intervals (e.g., every 5 minutes). Good for backups but might lose recent data if it crashes.
- **AOF (Append Only File)**: Logs every write operation. More durable (can log every second) but the file is larger and slower to restore.

### 3. Data Structures (The Power of Redis)
Redis is not just Key-Value. It supports:
- **String**: Basic text or binary data.
- **List**: Linked list of strings (Good for Timelines, Message Queues).
- **Set**: Unordered collection of unique strings (Good for Tags, Friends list).
- **Sorted Set (ZSet)**: Unique strings ordered by a score (Perfect for **Leaderboards**).
- **Hash**: Map between string fields and string values (Good for storing Objects/User Profiles).
- **Pub/Sub**: Publish/Subscribe messaging pattern.

### 4. Advanced Features
- **Transactions**: Supports atomic operations (`MULTI`, `EXEC`).
- **Lua Scripting**: Run server-side scripts.
- **Geospatial**: Store and query coordinates (Find users "near me").

---

## II. Memcached

Memcached is a simple, high-performance, distributed memory object caching system.

### 1. Architecture
- **Multi-Threaded**: This is the biggest difference. Memcached can use **multiple cores** and **multiple threads** to handle requests.
- **Vertical Scaling**: You can scale up (bigger instance type) effectively because it utilizes all CPU cores.

### 2. Data Model
- **Simple Key-Value**: It treats all data as "blob" objects. It doesn't understand Lists or Sets. It just stores bytes.
- **Transient**: RAM only. If you restart the server, data is GONE. No disk persistence.

### 3. Memory Management
- **Slab Allocation**: Memcached divides memory into chunks (slabs) of specific sizes. This prevents memory fragmentation but can lead to some wasted space if object sizes don't match slab sizes perfectly.
- **LRU (Least Recently Used)**: When memory is full, it aggressively evicts the oldest/least used data.

---

## III. When to choose what?

### Choose Redis if:
- You need **Data Persistence** (don't want to lose cache on restart).
- You need **High Availability** (Multi-AZ, Failover).
- You need complex data types (Lists, Sets, Sorted Sets for Leaderboards).
- You need Pub/Sub for chat apps.
- You need specific deletion policies or backup capabilities.

### Choose Memcached if:
- You need the **simplest** model possible.
- You need to cache simple objects (HTML fragments, DB rows).
- You need to handle extremely high concurrency with **Multi-threading** (Scale up on large instances).
- You don't care if data is lost upon restart.
