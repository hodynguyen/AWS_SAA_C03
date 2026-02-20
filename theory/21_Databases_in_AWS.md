[Vietnamese Below](#vietnamese-version)

# Databases in AWS

## 1. Choosing the Right Database

Choosing the right database depends on your **workload requirements**: structure, size, read/write patterns, durability, latency, and access patterns.

### Key Questions to Ask
*   Is your workload **read-heavy, write-heavy, or balanced**?
*   What **throughput** do you need? Will it fluctuate?
*   How much data do you store and for how long? Will it grow? Average object size?
*   What **data model**: relational, NoSQL, key-value, document, graph, time-series?
*   Do you need **strong consistency** or eventual consistency?
*   Do you need **structured data** (schema) or **flexible schema**?

### Database Types on AWS

| Type | AWS Service | Use Case |
|---|---|---|
| **Relational** | RDS, Aurora | Transactions, joins, structured data |
| **Key-Value** | DynamoDB | High throughput, low latency, flexible schema |
| **In-Memory** | ElastiCache | Caching, session store, leaderboards |
| **Document** | DocumentDB | JSON documents, MongoDB workloads |
| **Graph** | Neptune | Social networks, knowledge graphs, fraud detection |
| **Wide Column** | Keyspaces | Cassandra workloads, IoT |
| **Time Series** | Timestream | IoT, DevOps monitoring, time-series data |
| **Object Store** | S3 | Static files, backups, data lakes |
| **Warehouse** | Redshift | Analytics, OLAP, BI |
| **Search** | OpenSearch | Full-text search, log analytics |
| **Ledger** | QLDB | Immutable, cryptographically verifiable records |

## 2. Amazon RDS (Summary)

Managed **relational database** service.

### Key Points
*   **Engines**: PostgreSQL, MySQL, MariaDB, Oracle, SQL Server, IBM Db2.
*   **Managed**: Automated provisioning, patching, backups, Multi-AZ, Read Replicas.
*   **Storage**: Auto-scaling with **EBS** (gp2/gp3, io1/io2).
*   **Backup**: Automated (1–35 days retention), manual snapshots.
*   **Read Replicas**: Up to **15** replicas for read scaling (async replication).
*   **Multi-AZ**: Synchronous replication for **high availability** (failover).
*   **Security**: IAM authentication, Security Groups, KMS encryption, SSL/TLS.
*   **RDS Proxy**: Connection pooling for Lambda + RDS.

### Use Case
*   OLTP workloads, relational data with joins, SQL queries.
*   Applications needing ACID compliance.

## 3. Amazon Aurora (Summary)

AWS's **cloud-optimized relational database** — compatible with MySQL and PostgreSQL.

### Key Points
*   **5x** performance of MySQL, **3x** of PostgreSQL.
*   Storage auto-grows from **10GB to 128TB**.
*   Up to **15 Read Replicas** (faster replication than RDS).
*   **6 copies** of data across **3 AZs** (highly available).
*   **Aurora Serverless**: Auto-scaling, pay-per-use, good for unpredictable workloads.
*   **Aurora Global Database**: Cross-region replicas (< 1 second replication lag).
*   **Aurora Multi-Master**: Write to multiple nodes for write high availability.

### Use Case
*   Same as RDS but need **better performance, scalability, and availability**.
*   Drop-in replacement for MySQL/PostgreSQL.

## 4. Amazon ElastiCache (Summary)

Managed **in-memory data store** — Redis or Memcached.

### Key Points
*   **Sub-millisecond** latency for cached data.
*   **Redis**: Replication, Multi-AZ, Read Replicas, backup/restore, data persistence, Sets, Sorted Sets.
*   **Memcached**: Multi-threaded, no replication, no backup, simple caching.
*   Requires **code changes** in the application (not transparent caching like DAX).

### Use Cases
*   **Session store**: Store user sessions for stateless applications.
*   **Database cache**: Cache frequent queries to reduce RDS/Aurora load.
*   **Leaderboards**: Redis Sorted Sets for real-time rankings.

## 5. Amazon DynamoDB (Summary)

Fully managed **serverless NoSQL** key-value database.

### Key Points
*   **Serverless**: No servers to manage.
*   **Single-digit millisecond** latency at any scale.
*   **Capacity modes**: Provisioned (with Auto Scaling) or On-Demand.
*   **Max item size**: 400KB.
*   **DAX**: In-memory cache (microsecond latency, no code changes).
*   **Streams**: Ordered change log → trigger Lambda.
*   **Global Tables**: Multi-region, active-active replication.
*   **TTL**: Auto-expire items.
*   **Export/Import**: To/from S3 without affecting capacity.

### Use Cases
*   Serverless applications, high throughput, flexible schema.
*   Gaming leaderboards, IoT data, session management.

## 6. Amazon S3 (Summary)

**Object storage** — not a traditional database, but useful for many data patterns.

### Key Points
*   Store **objects** (up to 5TB each) in **buckets**.
*   Great for **static files**, backups, media, data lakes.
*   **Storage classes**: Standard, IA, One Zone-IA, Glacier, Glacier Deep Archive, Intelligent-Tiering.
*   **Max object size**: 5TB (multi-part upload for > 5GB).
*   **S3 Select / Athena**: Query data directly in S3 using SQL.
*   **Lifecycle policies**: Auto-transition between storage classes.

### Use Cases
*   Static assets, backups, data lakes, big data analytics.
*   Key-value store for **large objects** (not suitable for small items — use DynamoDB for that).

## 7. Amazon DocumentDB

Managed **document database** — AWS's **MongoDB-compatible** service.

### Key Points
*   Fully managed, highly available (replication across 3 AZs).
*   Storage auto-grows from **10GB to 64TB**.
*   Automatically scales to handle **millions of requests/second**.
*   Similar deployment concepts to Aurora (but for MongoDB).

### Use Case
*   Migrate from **MongoDB** to AWS.
*   Store, query, and index **JSON data**.

## 8. Amazon Neptune

Managed **graph database** service.

### Key Points
*   Optimized for storing and navigating **highly connected data** (billions of relationships).
*   Highly available across **3 AZs**, up to **15 Read Replicas**.
*   Supports graph models: **Property Graph** and **RDF** (SPARQL).

### Use Cases
*   **Social networking**: Friends, connections, recommendations.
*   **Knowledge graphs**: Wikipedia-style linked data.
*   **Fraud detection**: Detect suspicious patterns in relationships.

## 9. Amazon Keyspaces (for Apache Cassandra)

Managed **Apache Cassandra-compatible** database service.

### Key Points
*   **Serverless**, auto-scaling, fully managed.
*   Tables replicated **3 times across multiple AZs**.
*   Compatible with **CQL** (Cassandra Query Language).
*   **Capacity modes**: On-Demand or Provisioned (with Auto Scaling).

### Use Cases
*   Migrate from **Cassandra** to AWS.
*   **IoT** device data, time-series data at scale.

## 10. Amazon Timestream

Managed **time-series database** service.

### Key Points
*   **Serverless**, auto-scaling, fully managed.
*   Store and analyze **trillions of events per day**.
*   **1000x faster** and **1/10th the cost** of relational databases for time-series.
*   Built-in **time-series analytics functions** (smoothing, interpolation, approximation).
*   Data lifecycle: **recent data** in memory, **historical data** in cost-optimized storage (automatic).
*   Supports **SQL** for queries.

### Use Cases
*   **IoT** applications.
*   **DevOps** monitoring (metrics, logs).
*   **Real-time analytics** on time-stamped data.

### Exam Tips — Choosing the Right Database
*   **OLTP / SQL / Joins** → **RDS** or **Aurora**.
*   **High performance relational** → **Aurora**.
*   **Caching / Session store** → **ElastiCache**.
*   **Key-value / Serverless NoSQL** → **DynamoDB**.
*   **Object storage / Data lake** → **S3**.
*   **MongoDB compatible** → **DocumentDB**.
*   **Graph / Relationships** → **Neptune**.
*   **Cassandra compatible** → **Keyspaces**.
*   **Time-series / IoT metrics** → **Timestream**.
*   **Warehouse / Analytics / OLAP** → **Redshift**.
*   **Search / Log analytics** → **OpenSearch**.

---

<a id="vietnamese-version"></a>

# Databases trong AWS

## 1. Chọn đúng Database

Chọn database phù hợp phụ thuộc vào **yêu cầu workload**: cấu trúc, kích thước, patterns đọc/ghi, độ bền, độ trễ, và access patterns.

### Câu hỏi cần đặt ra
*   Workload **đọc nhiều, ghi nhiều, hay cân bằng**?
*   Cần **throughput** bao nhiêu? Có dao động không?
*   Lưu bao nhiêu dữ liệu, trong bao lâu? Có tăng trưởng không?
*   **Mô hình dữ liệu**: relational, NoSQL, key-value, document, graph, time-series?
*   Cần **strong consistency** hay eventual consistency?
*   Cần **structured data** (schema) hay **flexible schema**?

### Các loại Database trên AWS

| Loại | AWS Service | Use Case |
|---|---|---|
| **Relational** | RDS, Aurora | Transactions, joins, dữ liệu có cấu trúc |
| **Key-Value** | DynamoDB | Throughput cao, latency thấp, schema linh hoạt |
| **In-Memory** | ElastiCache | Caching, session store, leaderboards |
| **Document** | DocumentDB | JSON documents, workloads MongoDB |
| **Graph** | Neptune | Mạng xã hội, knowledge graphs, phát hiện gian lận |
| **Wide Column** | Keyspaces | Workloads Cassandra, IoT |
| **Time Series** | Timestream | IoT, DevOps monitoring, dữ liệu chuỗi thời gian |
| **Object Store** | S3 | Static files, backups, data lakes |
| **Warehouse** | Redshift | Analytics, OLAP, BI |
| **Search** | OpenSearch | Full-text search, log analytics |
| **Ledger** | QLDB | Records bất biến, xác minh mật mã |

## 2. Amazon RDS (Tóm tắt)

Dịch vụ **cơ sở dữ liệu quan hệ** được quản lý.

### Điểm chính
*   **Engines**: PostgreSQL, MySQL, MariaDB, Oracle, SQL Server, IBM Db2.
*   **Managed**: Tự động provisioning, patching, backups, Multi-AZ, Read Replicas.
*   **Storage**: Tự động scale với **EBS** (gp2/gp3, io1/io2).
*   **Backup**: Tự động (1–35 ngày), snapshot thủ công.
*   **Read Replicas**: Lên tới **15** replicas cho read scaling (async replication).
*   **Multi-AZ**: Replication đồng bộ cho **tính sẵn sàng cao** (failover).
*   **Bảo mật**: IAM authentication, Security Groups, KMS encryption, SSL/TLS.
*   **RDS Proxy**: Connection pooling cho Lambda + RDS.

### Use Case
*   Workloads OLTP, dữ liệu quan hệ với joins, SQL queries.

## 3. Amazon Aurora (Tóm tắt)

CSDL quan hệ **tối ưu cho cloud** của AWS — tương thích MySQL và PostgreSQL.

### Điểm chính
*   Hiệu suất **gấp 5 lần** MySQL, **gấp 3 lần** PostgreSQL.
*   Storage tự tăng từ **10GB đến 128TB**.
*   Lên tới **15 Read Replicas** (replication nhanh hơn RDS).
*   **6 bản sao** dữ liệu trên **3 AZs** (tính sẵn sàng cao).
*   **Aurora Serverless**: Tự động scale, trả theo dùng, tốt cho workloads không dự đoán.
*   **Aurora Global Database**: Replicas cross-region (độ trễ replication < 1 giây).
*   **Aurora Multi-Master**: Ghi vào nhiều nodes cho write HA.

### Use Case
*   Giống RDS nhưng cần **hiệu suất, scalability, và availability tốt hơn**.

## 4. Amazon ElastiCache (Tóm tắt)

**Lưu trữ dữ liệu trong bộ nhớ** được quản lý — Redis hoặc Memcached.

### Điểm chính
*   Độ trễ **dưới mili giây** cho dữ liệu cache.
*   **Redis**: Replication, Multi-AZ, Read Replicas, backup/restore, data persistence.
*   **Memcached**: Multi-threaded, không replication, không backup, caching đơn giản.
*   Cần **thay đổi code** trong ứng dụng (không phải transparent caching như DAX).

### Use Cases
*   **Session store**: Lưu sessions cho ứng dụng stateless.
*   **Database cache**: Cache queries thường xuyên để giảm tải RDS/Aurora.
*   **Leaderboards**: Redis Sorted Sets cho bảng xếp hạng real-time.

## 5. Amazon DynamoDB (Tóm tắt)

CSDL **NoSQL serverless** key-value được quản lý hoàn toàn.

### Điểm chính
*   **Serverless**: Không quản lý servers.
*   Độ trễ **mili giây đơn** ở mọi quy mô.
*   **Capacity modes**: Provisioned (có Auto Scaling) hoặc On-Demand.
*   **Item tối đa**: 400KB.
*   **DAX**: Cache trong bộ nhớ (microsecond, không đổi code).
*   **Streams**: Log thay đổi có thứ tự → trigger Lambda.
*   **Global Tables**: Multi-region, active-active.
*   **TTL**: Tự xóa items hết hạn.

### Use Cases
*   Ứng dụng serverless, throughput cao, schema linh hoạt.

## 6. Amazon S3 (Tóm tắt)

**Object storage** — không phải database truyền thống, nhưng hữu ích cho nhiều data patterns.

### Điểm chính
*   Lưu **objects** (tối đa 5TB mỗi object) trong **buckets**.
*   Tốt cho **static files**, backups, media, data lakes.
*   **Storage classes**: Standard, IA, One Zone-IA, Glacier, Deep Archive, Intelligent-Tiering.
*   **S3 Select / Athena**: Query dữ liệu trực tiếp trong S3 bằng SQL.

### Use Cases
*   Static assets, backups, data lakes, big data analytics.
*   Key-value store cho **objects lớn** (items nhỏ → dùng DynamoDB).

## 7. Amazon DocumentDB

CSDL **document** được quản lý — dịch vụ **tương thích MongoDB** của AWS.

### Điểm chính
*   Fully managed, tính sẵn sàng cao (replication trên 3 AZs).
*   Storage tự tăng từ **10GB đến 64TB**.
*   Tự động scale xử lý **hàng triệu requests/giây**.
*   Khái niệm deploy tương tự Aurora (nhưng cho MongoDB).

### Use Case
*   Migrate từ **MongoDB** sang AWS.
*   Lưu trữ, query, và index **dữ liệu JSON**.

## 8. Amazon Neptune

Dịch vụ **graph database** được quản lý.

### Điểm chính
*   Tối ưu cho lưu trữ và duyệt **dữ liệu có kết nối cao** (hàng tỷ relationships).
*   Tính sẵn sàng cao trên **3 AZs**, lên tới **15 Read Replicas**.
*   Hỗ trợ: **Property Graph** và **RDF** (SPARQL).

### Use Cases
*   **Mạng xã hội**: Bạn bè, kết nối, đề xuất.
*   **Knowledge graphs**: Dữ liệu liên kết kiểu Wikipedia.
*   **Phát hiện gian lận**: Phát hiện patterns đáng ngờ trong relationships.

## 9. Amazon Keyspaces (cho Apache Cassandra)

Dịch vụ CSDL **tương thích Apache Cassandra** được quản lý.

### Điểm chính
*   **Serverless**, tự động scale, fully managed.
*   Tables replicated **3 lần trên nhiều AZs**.
*   Tương thích **CQL** (Cassandra Query Language).
*   **Capacity modes**: On-Demand hoặc Provisioned (có Auto Scaling).

### Use Cases
*   Migrate từ **Cassandra** sang AWS.
*   Dữ liệu thiết bị **IoT**, time-series ở quy mô lớn.

## 10. Amazon Timestream

Dịch vụ **time-series database** được quản lý.

### Điểm chính
*   **Serverless**, tự động scale, fully managed.
*   Lưu và phân tích **hàng nghìn tỷ events mỗi ngày**.
*   **Nhanh gấp 1000 lần** và **chi phí bằng 1/10** so với CSDL quan hệ cho time-series.
*   Tích hợp **hàm phân tích time-series** (smoothing, interpolation, approximation).
*   Lifecycle: **Dữ liệu mới** trong memory, **dữ liệu cũ** trong storage tiết kiệm (tự động).
*   Hỗ trợ **SQL** cho queries.

### Use Cases
*   Ứng dụng **IoT**.
*   **DevOps** monitoring (metrics, logs).
*   **Analytics real-time** trên dữ liệu có timestamp.

### Exam Tips — Chọn đúng Database
*   **OLTP / SQL / Joins** → **RDS** hoặc **Aurora**.
*   **Hiệu suất relational cao** → **Aurora**.
*   **Caching / Session store** → **ElastiCache**.
*   **Key-value / Serverless NoSQL** → **DynamoDB**.
*   **Object storage / Data lake** → **S3**.
*   **Tương thích MongoDB** → **DocumentDB**.
*   **Graph / Relationships** → **Neptune**.
*   **Tương thích Cassandra** → **Keyspaces**.
*   **Time-series / IoT metrics** → **Timestream**.
*   **Warehouse / Analytics / OLAP** → **Redshift**.
*   **Search / Log analytics** → **OpenSearch**.
