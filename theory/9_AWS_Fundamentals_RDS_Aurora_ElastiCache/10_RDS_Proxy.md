# RDS Proxy

## 1. Problem (The "Database Storm")
In modern serverless architectures (like AWS Lambda), applications can scale up very quickly.
- Imagine 10,000 users access your app simultaneously.
- Lambda spawns 10,000 functions.
- Each function opens a connection to the RDS database.
- **Result**: RDS runs out of memory/CPU trying to manage 10,000 open connections. The database crashes.

## 2. Solution: RDS Proxy
RDS Proxy acts as an intermediary (middleman) between your application and the database.

### Key Feature: Connection Pooling
- Instead of opening a new connection for every request, RDS Proxy maintains a **pool** of established connections to the database.
- When Lambda needs to query:
  1. It connects to the Proxy.
  2. The Proxy reuses an existing idle connection from the pool to talk to the DB.
  3. After the query, the connection is returned to the pool (not closed).
- **Benefit**: 10,000 Lambda functions might effectively use only 50 actual DB connections.

## 3. Other Benefits
- **Improved Failover (High Availability)**:
  - If the RDS instance fails over (Multi-AZ), the Proxy holds the client connections while switching the backend to the new Standby.
  - Reduces failover time from ~30s (DNS propagation) to **< 10s**.
- **Security**:
  - Enforces **IAM Authentication** (Lambda authenticates to Proxy via IAM, Proxy authenticates to DB via Secrets Manager).
  - You never need to hardcode DB passwords in Lambda code.

## 4. When to use?
- With **AWS Lambda** (Serverless).
- When you have a massive number of open connections (Connection storm).
- When you need faster failover recovery.
