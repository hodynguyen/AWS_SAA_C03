# Redis Features & Real-world Applications

## 1. Pub/Sub (Publish/Subscribe)
### Concept
A messaging pattern where senders (publishers) send messages to specific channels, and receivers (subscribers) listen to those channels. Redis does not store these messages; it just forwards them instantly.

### Use Case: Real-time Notification / Chat
**Scenario**: When User A comments on a post, notify User B instantly on the website.
**Implementation**:
1.  **User B's Browser**: Opens a WebSocket connection to the Backend server (e.g., Node.js).
2.  **Backend**: Subscribes to Redis channel `notifications:user_B`.
    *   Command: `SUBSCRIBE notifications:user_B`
3.  **User A**: Comments on the post.
4.  **Backend (API)**: Publishes a message to Redis.
    *   Command: `PUBLISH notifications:user_B '{"msg": "User A commented..."}'`
5.  **Result**: Redis pushes the message to the listening Backend -> Backend pushes to User B's WebSocket -> Notification pops up.

---

## 2. Geospatial (Geo)
### Concept
Redis can store coordinates (Longitude, Latitude) and calculate distances or find members within a radius. It uses `Sorted Sets` under the hood.

### Use Case: "Find Drivers Near Me" (Uber/Grab)
**Scenario**: You open the app and want to see all taxis within 5km.
**Implementation**:
1.  **Driver App**: Updates location every 5 seconds.
    *   Command: `GEOADD drivers:city_hanoi 105.8 21.0 "Driver_1"`
2.  **User App**: Requests drivers nearby.
    *   Command: `GEORADIUS drivers:city_hanoi 105.8 21.0 5 km WITHDIST`
3.  **Result**: Redis returns a list of Driver IDs and their distance instantly.

---

## 3. Bitmaps
### Concept
Bitmaps allow you to manipulate individual bits (0 or 1) inside a String key. Extremely memory efficient.

### Use Case: User Online Status / Daily Active Users (DAU)
**Scenario**: Track which of your 100 million users logged in today.
**Old Way**: Store distinct user IDs in a Set. (100M users * 4 bytes = 400MB RAM).
**Redis Way**:
- Create a key `active:2024-01-27`. Use User ID as the bit offset.
- **Implementation**:
    1.  User ID 50 logs in: `SETBIT active:2024-01-27 50 1`
    2.  User ID 99 logs in: `SETBIT active:2024-01-27 99 1`
- **Count Total**: `BITCOUNT active:2024-01-27`.
- **Memory Cost**: 100 million bits = Only ~12MB RAM. (Saving 97% RAM).

---

## 4. HyperLogLog (HLL)
### Concept
A probabilistic data structure used to count unique items (Cardinality) with very little memory. Even with billions of items, it only takes 12KB.

### Use Case: Unique Views Counter (Youtube)
**Scenario**: Count how many *unique* IPs viewed a video.
**Implementation**:
1.  User watches video: `PFADD video:123:views "1.2.3.4"`
2.  Get Count: `PFCOUNT video:123:views`
3.  **Trade-off**: The count is an estimate (0.81% error rate). But for 1 billion views, knowing it's roughly 1,000,000,000 vs 1,000,005,000 doesn't matter, saving terabytes of RAM is more important.

---

## 5. Lua Scripting
### Concept
Allows executing logic *inside* Redis server atomically.

### Use Case: Complex Atomic Operations (Inventory Check)
**Scenario**: User buys an item. Need to check stock > 0 AND deduct stock.
**Problem**:
1. App: `GET stock` (returns 1).
2. App: `DECR stock`.
*Race Condition*: If 2 users do step 1 same time, both see stock=1, both buy -> Stock becomes -1.
**Redis Lua Solution**:
- Write a Lua script:
  ```lua
  local stock = redis.call("GET", KEYS[1])
  if tonumber(stock) > 0 then
      redis.call("DECR", KEYS[1])
      return 1 -- Success
  else
      return 0 -- Fail
  end
  ```
- Run it: `EVAL script 1 product:123`
- **Result**: Thread-safe guarantee. No one can interrupt the script while running.

---

## 6. Redis Streams (Since Redis 5.0)
### Concept
An append-only log data structure, similar to Apache Kafka but lighter. Supports "Consumer Groups".

### Use Case: Activity Feed / Event Sourcing
**Scenario**: A user places an Order. Multiple services need to know (Email Service, Inventory Service, Analytics Service).
**Implementation**:
1.  **Order Service**: Adds event into stream.
    *   `XADD orders_stream * user_id 1 product_id 99`
2.  **Email Worker**: Reads from stream and sends email.
    *   `XREADGROUP GROUP emails ...`
3.  **Inventory Worker**: Reads same stream and updates stock.
4.  **Feature**: If Email Worker crashes, the message is not lost. It stays in the stream until acknowledged (`XACK`).
