[Vietnamese Below](#vietnamese-version)

# Amazon RDS, Aurora & ElastiCache - Cheat Sheet

## 1. Amazon RDS (Relational Database Service)

**Concept**: Distributed Relational Database Service (Managed Service).
**Supported Engines**: Postgres, MySQL, MariaDB, Oracle, Microsoft SQL Server, Aurora (AWS proprietary).

**Key Features**:
*   **Managed Service**: AWS handles provisioning, patching, backup, recovery, failure detection, and repair.
*   **Storage Auto Scaling**: You can increase storage limits and it will automatically scale when full.
*   **Backups**:
    *   **Automated Backups**: Daily automatic backup + transaction logs (last 5 minutes retention). Retention period: 1-35 days.
    *   **Snapshots**: Manual backup (user triggered). Exists permanently until you delete it.

### RDS Backups & Restore (Important)
*   **Automated Backups**:
    *   Performed daily (during your chosen backup window).
    *   Transaction logs backed up every 5 minutes.
    *   **Retention Period**: Default 7 days, max 35 days. (Set to 0 to disable).
    *   When restoring: Creates a **new DB Instance** (does not overwrite the old DB).
*   **DB Snapshots (Manual)**:
    *   Triggered by user. Exists indefinitely (even if original DB is deleted).
    *   Can share snapshot with other AWS accounts or copy to another Region.

### RDS Multi-AZ vs Read Replicas (IMPORTANT)
This is a VERY common topic in the exam. Distinguish clearly between High Availability (Multi-AZ) and Scalability (Read Replicas).

| Feature | RDS Multi-AZ (Standby) | Read Replicas |
| :--- | :--- | :--- |
| **Purpose** | **High Availability (HA)**, Disaster Recovery (DR) | **Scalability** (Scale read capacity) |
| **Replication Mechanism** | **Synchronous** to standby | **Asynchronous** |
| **Active/Passive** | One primary DB (Active), one standby DB (Passive) - **cannot read from standby** | All replicas are **readable** |
| **Failover** | **Automatic** failover to standby if master dies | Must manually promote to Master if main dies (or use for DR) |
| **Region** | Same Region (different AZ) | Can be **Cross-Region** (for DR or reducing read latency in another region) |
| **Backups** | Automated backups taken from standby (reduce I/O load on master) | Not applicable |

### RDS Security
*   **Encryption**:
    *   **At rest**: Uses AWS KMS (AES-256). **Must be defined at Launch time**.
    *   **In transit**: Uses SSL certificates.
    *   **Note**: If master is unencrypted, read replicas cannot be encrypted. To encrypt an unencrypted DB: Snapshot -> Copy Snapshot as Encrypted -> Restore DB from Encrypted Snapshot.
*   **IAM Authentication**:
    *   Can use IAM roles to authenticate to **MySQL** and **PostgreSQL** instead of DB passwords.
*   **Security Groups**: Controls network access (open port 3306, 5432,...).

### RDS Proxy
*   **Purpose**: Fully managed, highly available (HA) database proxy for RDS.
*   **Why use?**
    *   **Connection Pooling**: Reduces load on DB by pooling and sharing connections (very good for **Lambda** architecture).
    *   **Faster Failover**: Reduces failover time by up to 66%.
    *   **Security**: Enforces IAM authentication and stores credentials in Secrets Manager.

## 2. Amazon Aurora

**Concept**: AWS "homegrown" relational database, compatible with MySQL and PostgreSQL. Cloud-native, high performance (5x faster than MySQL, 3x faster than Postgres).

### Architecture & Reliability
*   **Shared Storage Volume**: Data automatically scales in 10GB chunks, up to 128TB.
*   **Replication**:
    *   6 copies of data across **3 AZs** (2 copies per AZ).
    *   Very durable: Lose 2 copies -> can still write (write availability), Lose 3 copies -> can still read (read availability).
    *   **Self-healing**: Automatically detects and repairs bad data blocks.
*   **Aurora Backups**:
    *   Automatic, continuous (no performance impact).
    *   **Point-in-Time Recovery (PITR)**: Restore to any second within retention period.
    *   No complex manual snapshot management needed like RDS.
*   **Cloning**: Create new DB clone from existing DB extremely fast (uses copy-on-write mechanism) - Very useful for Test/Staging environments.

### Scaling in Aurora
*   **Aurora Replicas**: Max **15** read replicas. Replica lag extremely low (< 10ms).
*   **Writer Endpoint**: Points to master instance.
*   **Reader Endpoint**: Automatically load balances connections to all read replicas.
*   **Auto Scaling**: Automatically adds/removes read replicas based on CPU/Connections.

### Advanced Features
*   **Aurora Serverless**:
    *   Automatically starts and scales capacity based on actual demand.
    *   Good for infrequent or unpredictable workloads.
*   **Aurora Global Database**:
    *   Cross-Region Replication (latency < 1 second).
    *   1 Hot Primary Region (R/W), max 5 Secondary Regions (RO).
    *   Promote secondary region to primary in < 1 minute (Disaster Recovery).
*   **Aurora Custom**: Allows access to underlying OS (for legacy apps needing OS privileges).

## 3. Amazon ElastiCache

**Concept**: Managed in-memory data store (RAM). Helps accelerate data retrieval (sub-millisecond latency).

### Redis vs Memcached

| Feature | Redis | Memcached |
| :--- | :--- | :--- |
| **Data Types** | **Complex**: Strings, Hashes, Lists, Sets, Sorted Sets, Bitmaps... | **Simple**: String (Key-Value) |
| **Persistence** | **Yes** (AOF, RDB) - keeps data on restart | **No** (Data lost on restart) |
| **Multi-AZ** | **Yes** (Replication, Auto-failover) | **No** (Sharding only) |
| **Pub/Sub** | **Yes** | **No** |
| **Sorting/Ranking** | **Yes** (Sorted Sets - Used for Leaderboards) | **No** |
| **Use Cases** | Leaderboards, complex caching, session store, chat, geospatial | Simple caching, multithreaded architecture (scaling up) |

> **Exam Tip**: If the question mentions "Multi-AZ", "Backup", "Restore", or "Complex Data Types" -> Choose **Redis**. If it mentions "Simple Caching", "Multithreading" -> Choose **Memcached**.

### Backup & Restore for ElastiCache
*   **Redis**:
    *   Supports Backup & Restore (Snapshots).
    *   Can setup automatic daily backups.
    *   Uses RDB file for restore.
*   **Memcached**:
    *   **NO** backup support. Data is purely on RAM and lost when node is terminated.

### Caching Strategies
*   **Lazy Loading**: Only load data into cache when needed (cache miss).
    *   *Pros*: Only caches used data. *Cons*: Slow initial access (App->Cache(miss)->DB->Cache). Data can become stale.
*   **Write-Through**: Add/Update data in cache as soon as it's written to DB.
    *   *Pros*: Data in cache is always fresh. *Cons*: Slower write (write to 2 places). Wasted if data is rarely read again.

### Common Use Cases
*   **Database Caching**: Offload read traffic from RDS.
*   **Session Store**: Store user sessions (for stateless apps).

## 4. Important Ports to Remember

| Service | Protocol | Port(s) |
| :--- | :--- | :--- |
| PostgreSQL | TCP | 5432 |
| MySQL / MariaDB / Aurora | TCP | 3306 |
| Oracle | TCP | 1521 |
| SQL Server | TCP | 1433 |
| Redis | TCP | 6379 |
| Memcached | TCP | 11211 |

## 5. Exam Hints

*   **RDS vs Aurora**: Prioritize **Aurora** for "High Availability", "Performance", or "Serverless" requirements unless specified otherwise (e.g., must use Oracle/SQL Server).
*   **Read Performance Issue?** -> Add **Read Replicas** (RDS/Aurora) or use **ElastiCache**.
*   **Disaster Recovery (Region failure)?** -> Use **RDS Read Replicas (Cross-Region)** or **Aurora Global Database**.
*   **Lambda "Too many connections" error?** -> Use **RDS Proxy**.
*   **Store User Sessions?** -> Use **ElastiCache (Redis)** or DynamoDB.

---

<a id="vietnamese-version"></a>

# Amazon RDS (Relational Database Service)

**Khái niệm**: Dịch vụ cơ sở dữ liệu quan hệ phân tán (Managed Service).
**Các Engine hỗ trợ**: Postgres, MySQL, MariaDB, Oracle, Microsoft SQL Server, Aurora (Của riêng AWS).

**Tính năng chính**:
*   **Managed Service**: AWS lo việc provisioning, vá lỗi (patching), backup, phục hồi, phát hiện lỗi và sửa chữa.
*   **Storage Auto Scaling**: Bạn có thể tăng giới hạn lưu trữ và nó sẽ tự động scale khi đầy.
*   **Backups**:
    *   **Automated Backups**: Tự động backup hàng ngày + transaction logs (lưu giữ 5 phút cuối). Thời hạn lưu trữ: 1-35 ngày.
    *   **Snapshots**: Backup thủ công (do user kích hoạt). Tồn tại mãi mãi cho đến khi bạn xóa.

### RDS Backups & Restore (Quan trọng)
*   **Automated Backups (Tự động)**:
    *   Thực hiện hàng ngày (trong backup window do bạn chọn).
    *   Transaction logs được backup mỗi 5 phút.
    *   **Retention Period**: Mặc định 7 ngày, tối đa 35 ngày. (Set 0 để tắt).
    *   Khi restore: Tạo ra một **DB Instance mới** (không đè lên DB cũ).
*   **DB Snapshots (Thủ công)**:
    *   Do người dùng trigger. Tồn tại vô thời hạn (kể cả khi xóa DB gốc).
    *   Có thể chia sẻ snapshot với tài khoản AWS khác hoặc copy sang Region khác.

### RDS Multi-AZ và Read Replicas (IMPORTANT)
Đây là chủ đề RẤT hay gặp trong kỳ thi. Cần phân biệt rõ giữa High Availability (Multi-AZ) và Scalability (Read Replicas).

| Tính năng | RDS Multi-AZ (Standby) | Read Replicas |
| :--- | :--- | :--- |
| **Mục đích** | **High Availability (HA)** (Tính sẵn sàng cao), Disaster Recovery (DR) | **Scalability** (Mở rộng khả năng đọc) |
| **Cơ chế Replication** | **Synchronous** (Đồng bộ) sang standby | **Asynchronous** (Bất đồng bộ) |
| **Active/Passive** | Một DB chính (Active), một DB dự phòng (Standby) - **không thể đọc từ standby** | Tất cả bản sao đều có thể **đọc** được |
| **Failover** | **Tự động** failover sang standby nếu master chết | Phải thủ công promote lên thành Master nếu main chết (hoặc dùng cho DR) |
| **Vùng (Regions)** | Cùng Region (khác AZ) | Có thể là **Cross-Region** (cho DR hoặc giảm latency đọc ở region khác) |
| **Backups** | Automated backups được lấy từ standby (giảm tải I/O cho master) | Không áp dụng |

### RDS Security
*   **Encryption (Mã hóa)**:
    *   **At rest**: Sử dụng AWS KMS (AES-256). **Phải được định nghĩa lúc tạo DB (Launch time)**.
    *   **In transit**: Dùng SSL certificates.
    *   **Lưu ý**: Nếu master không mã hóa, read replicas cũng không thể mã hóa. Muốn mã hóa DB đang không mã hóa: Snapshot -> Copy Snapshot as Encrypted -> Restore DB từ Encrypted Snapshot.
*   **IAM Authentication**:
    *   Có thể dùng IAM roles để xác thực vào **MySQL** và **PostgreSQL** thay vì dùng mật khẩu DB.
*   **Security Groups**: Kiểm soát truy cập mạng (mở port 3306, 5432,...).

### RDS Proxy
*   **Mục đích**: Database proxy được quản lý hoàn toàn, tính sẵn sàng cao (HA) cho RDS.
*   **Tại sao dùng?**
    *   **Connection Pooling**: Giảm tải cho DB bằng cách gộp và chia sẻ kết nối (rất tốt cho kiến trúc **Lambda**).
    *   **Faster Failover**: Giảm thời gian failover tới 66%.
    *   **Security**: Bắt buộc dùng IAM authentication và lưu credentials trong Secrets Manager.

## 2. Amazon Aurora

**Khái niệm**: Database quan hệ "cây nhà lá vườn" của AWS, tương thích MySQL và PostgreSQL. Cloud-native, hiệu năng cao (nhanh gấp 5x MySQL, 3x Postgres).

### Kiến trúc & Độ tin cậy (Architecture & Reliability)
*   **Shared Storage Volume**: Dữ liệu tự động mở rộng theo chunk 10GB, tối đa 128TB.
*   **Replication**:
    *   6 bản copy dữ liệu nằm trên **3 AZs** (2 bản mỗi AZ).
    *   Rất bền bỉ: Mất 2 bản copy vẫn ghi được (write availability), mất 3 bản vẫn đọc được (read availability).
    *   **Self-healing**: Tự động phát hiện và sửa các khối dữ liệu hỏng.
*   **Aurora Backups**:
    *   Tự động, liên tục (không ảnh hưởng hiệu năng).
    *   **Point-in-Time Recovery (PITR)**: Restore về bất kỳ thời điểm nào trong retention period.
    *   Không cần quản lý snapshot thủ công phức tạp như RDS.
*   **Cloning**: Tạo bản sao DB mới từ DB hiện tại cực nhanh (dùng cơ chế copy-on-write) - Rất hữu ích cho môi trường Test/Staging.

### Scaling trong Aurora
*   **Aurora Replicas**: Tối đa **15** read replicas. Replica lag cực thấp (< 10ms).
*   **Writer Endpoint**: Trỏ tới master instance.
*   **Reader Endpoint**: Tự động cân bằng tải (load balance) kết nối tới tất cả read replicas.
*   **Auto Scaling**: Tự động thêm/bớt read replicas dựa trên CPU/Connections.

### Các tính năng nâng cao
*   **Aurora Serverless**:
    *   Tự động khởi tạo và scale capacity dựa trên nhu cầu thực tế.
    *   Tốt cho các workload không thường xuyên hoặc khó đoán trước.
*   **Aurora Global Database**:
    *   Cross-Region Replication (latency < 1 giây).
    *   1 Hot Primary Region (R/W), tối đa 5 Secondary Regions (RO).
    *   Promote region phụ lên thành chính trong < 1 phút (Disaster Recovery).
*   **Aurora Custom**: Cho phép truy cập vào OS bên dưới (dành cho các app legacy cần quyền OS).

## 3. Amazon ElastiCache

**Khái niệm**: Kho lưu trữ dữ liệu in-memory (RAM) được quản lý. Giúp tăng tốc độ đọc dữ liệu (độ trễ sub-millisecond).

### Redis vs Memcached

| Tính năng | Redis | Memcached |
| :--- | :--- | :--- |
| **Kiểu dữ liệu** | **Phức tạp**: Strings, Hashes, Lists, Sets, Sorted Sets, Bitmaps... | **Đơn giản**: String (Key-Value) |
| **Persistence (Lưu trữ)** | **Có** (AOF, RDB) - giữ dữ liệu khi restart | **Không** (Dữ liệu mất khi tắt) |
| **Multi-AZ** | **Có** (Replication, Auto-failover) | **Không** (Chỉ có Sharding) |
| **Pub/Sub** | **Có** | **Không** |
| **Sorting/Ranking** | **Có** (Sorted Sets - Dùng làm Bảng xếp hạng/Leaderboards) | **Không** |
| **Use Cases** | Leaderboards, caching phức tạp, session store, chat, geospatial | Caching đơn giản, kiến trúc multithreaded (scaling up) |

> **TIP Mẹo thi**: Nếu đề bài nhắc đến "Multi-AZ", "Backup", "Restore", hoặc "Complex Data Types" (kiểu dữ liệu phức tạp) -> Chọn **Redis**. Nếu nhắc đến "Simple Caching", "Multithreading" -> Chọn **Memcached**.

### Backup & Restore cho ElastiCache
*   **Redis**:
    *   Hỗ trợ Backup và Restore (Snapshots).
    *   Có thể setup tự động backup hàng ngày.
    *   Dùng file RDB để restore.
*   **Memcached**:
    *   **KHÔNG** hỗ trợ backup. Dữ liệu hoàn toàn trên RAM và mất khi node bị terminate.

### Chiến lược Caching (Caching Strategies)
*   **Lazy Loading**: Chỉ load dữ liệu vào cache khi cần (cache miss).
    *   *Ưu*: Chỉ cache dữ liệu được dùng. *Nhược*: Chậm lần đầu (App->Cache(miss)->DB->Cache). Dữ liệu có thể bị cũ (stale).
*   **Write-Through**: Thêm/Sửa dữ liệu vào cache ngay khi ghi vào DB.
    *   *Ưu*: Dữ liệu trong cache luôn mới. *Nhược*: Ghi chậm hơn (ghi 2 nơi). Lãng phí nếu dữ liệu ít khi được đọc lại.

### Use Cases phổ biến
*   **Database Caching**: Giảm tải đọc cho RDS.
*   **Session Store**: Lưu user session (cho các ứng dụng stateless).

## 4. Các Port quan trọng cần nhớ
| Service | Protocol | Port(s) |
| :--- | :--- | :--- |
| PostgreSQL | TCP | 5432 |
| MySQL / MariaDB / Aurora | TCP | 3306 |
| Oracle | TCP | 1521 |
| SQL Server | TCP | 1433 |
| Redis | TCP | 6379 |
| Memcached | TCP | 11211 |

## 5. Tổng kết mẹo thi (Exam Hints)
*   **RDS vs Aurora**: Ưu tiên **Aurora** cho các yêu cầu "High Availability", "Performance", hoặc "Serverless" trừ khi có yêu cầu đặc biệt (ví dụ: bắt buộc dùng Oracle/SQL Server).
*   **Vấn đề về hiệu năng đọc (Read performance)?** -> Thêm **Read Replicas** (RDS/Aurora) hoặc dùng **ElastiCache**.
*   **Disaster Recovery (Region failure)?** -> Dùng **RDS Read Replicas (Cross-Region)** hoặc **Aurora Global Database**.
*   **Lambda bị lỗi "Too many connections"?** -> Dùng **RDS Proxy**.
*   **Lưu User Sessions?** -> Dùng **ElastiCache (Redis)** hoặc DynamoDB.
