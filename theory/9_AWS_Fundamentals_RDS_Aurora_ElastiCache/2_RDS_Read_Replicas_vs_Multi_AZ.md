# RDS Read Replicas vs. Multi-AZ

## 1. RDS Read Replicas (Read Scalability)

### Purpose
- Used to **scale read workload** of your database.
- If your application performs many `SELECT` statements (heavy read traffic), create Read Replicas and point the application to read from them.

### Key Characteristics
- **Scaling:** Up to **15 Read Replicas**.
- **Replication Method:** **Asynchronous** replication (from Primary to Replica).
    - Writes happen to Primary -> Async copy to Replica.
    - **Replication Lag:** There can be a delay (seconds or minutes) before data appears in the Replica.
- **Connectivity:** Each Read Replica has its **own DNS Endpoint**.
    - You must update your application connection string to route read queries to the Replica endpoint.
- **Promotion:** A Read Replica can be promoted to become its own Standalone DB (useful for DR or Reporting).

### Deployment Options
- **Same AZ:** Free data transfer.
- **Cross AZ:** High availability for reads.
- **Cross Region:**
    - Higher copy cost.
    - Used for **Disaster Recovery (DR)** (promote replica in another region if main region fails).
    - Used to serve local data to users in a different part of the world (lower latency).

---

## 2. RDS Multi-AZ (High Availability)

### Purpose
- Used for **High Availability (HA)** and **Disaster Recovery**.
- Ensures database continuity in case of hardware failure, OS issues, or AZ outage.
- **NOT** used for performance scaling.

### Key Characteristics
- **Replication Method:** **Synchronous** replication.
    - Write to Primary -> Sync copy to Standby -> Confirm Write.
    - Ensures **Zero Data Loss** if failover occurs.
    - Slightly higher write latency due to sync wait.
- **Standby Instance:**
    - One DNS name (Endpoint) for the database.
    - **Invisible Standby:** You **CANNOT** access the standby instance (no read/write). It is just waiting for a failover.
- **Automatic Failover:**
    - If Primary fails, AWS automatically points the DNS endpoint to the Standby.
    - **No manual intervention needed**. No app code changes needed.

---

## 3. Comparison Cheat Sheet

| Feature | Read Replicas | Multi-AZ |
| :--- | :--- | :--- |
| **Primary Goal** | **Read Scalability** | **High Availability / DR** |
| **Replication** | Asynchronous (Eventual Consistency) | Synchronous (Strong Consistency) |
| **Number of Copies** | Up to 15 | 1 Standby |
| **Access** | Can be used for **SELECT** (Read) | **No Access** (Idle standby) |
| **Failover** | Manual (Must promote to use for writes) | **Automatic** |
| **Performance Impact** | Reduces Read load on Primary | May increase Write latency slightly |
| **Backups** | Taken from Replicas (optional) | Taken from Standby (to avoid IO freeze) |
| **Pricing** | Pay for extra instances + Data Transfer (if Cross Region) | Standard Multi-AZ pricing (usually 2x Single-AZ) |
