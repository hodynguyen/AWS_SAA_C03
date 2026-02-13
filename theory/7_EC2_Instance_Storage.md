[Vietnamese Below](#vietnamese-version)

# EC2 Storage

## 1. EBS Volume Types - (Memorize this)

EBS is a network drive, limited to **1 AZ**.

| Volume Type | Code Name | Specs (IOPS) - Memorize | Exam Keyword | Use Case |
| :--- | :--- | :--- | :--- | :--- |
| **General Purpose** | **gp3** (New), **gp2** | Max 16,000 IOPS. gp3: 3,000 free IOPS. gp2: 3 IOPS/GB (max 16k). | "Balance price/perf", "Boot volume", "System/Virtual desktop" | Default for most workloads. **gp3** decouples IOPS and Size config. |
| **Provisioned IOPS** | **io1 / io2** | Max 64,000 (io1) / 256,000 (io2) IOPS. | "Mission-critical", "Sub-millisecond latency", "> 16,000 IOPS" | Large Databases (Oracle, SAP HANA, SQL Server) needing extremely fast and stable I/O. |
| **Throughput Opt HDD** | **st1** | Max 500 MB/s throughput. (Low IOPS - 500). | "Big Data", "Data Warehouse", "Log processing", "Sequential I/O" | Large data processing (Kafka, Splunk, Hadoop). **Cannot be Boot Volume.** |
| **Cold HDD** | **sc1** | Max 250 MB/s throughput. (Low IOPS - 250). | "Lowest cost", "Archive", "Infrequently accessed" | Storing infrequently accessed data, cheap File servers. |

**Gold Rule**: Only SSD (gp, io) can be Boot Volumes (Windows/Linux installation). HDD (st, sc) are only for data storage.

## 2. EC2 Instance Store (Ephemeral Storage)

This is **physical** storage directly attached to the server (Hardware attached).
*   **Characteristics**:
    *   **Speed**: Terrific (much faster than EBS as it's not over network).
    *   **Durability**: Poor. **Data is lost** if you Stop/Start the machine (because the machine moves to another physical host).
*   **Exam Keywords**: "High performance", "Temporary storage", "Cache", "Buffer", "Scratch data".
*   **Note**: Do not use for long-term Database storage (unless using replication like Cassandra/MongoDB).

## 3. Amazon EFS (Elastic File System)

Shared network drive (Network File System - NFS).
*   **Characteristics**:
    *   **Multi-AZ**: Data automatically backed up across multiple AZs -> Very safe.
    *   **Share**: Thousands of EC2s can mount simultaneously.
    *   **Elastic**: Automatically expands/shrinks capacity (Pay per use).
    *   **Linux Only**: distinct from FSx (Windows).
*   **Performance Mode**:
    *   **General Purpose**: Default (Web server, CMS).
    *   **Max I/O**: Big Data, high parallelism.

## 4. EBS Multi-Attach

*   Allows attaching 1 EBS volume to multiple EC2s (same AZ).
*   Only supports: **io1, io2**.
*   **Use case**: Cluster application (app manages write synchronization), Clustered Database.
*   **Note**: Standard file systems (ext4, xfs) won't work, must use Cluster-aware file system (like GFS2).

## 5. EBS Encryption

*   Comprehensive encryption: Data at rest, Data in-flight, Snapshots are all encrypted.
*   **Minimal Impact**: Negligible impact on speed (latency).
*   **Exam Tip**: How to encrypt an Unencrypted volume?
    1.  Create Snapshot of old volume.
    2.  Copy Snapshot and check "Encrypt".
    3.  Create new volume from Encrypted Snapshot.
    4.  Attach new volume to instance.

## 6. EBS Snapshots (Backups) - Highly Tested

*   **Incremental**: Only saves **changed** data compared to previous -> Saves money & time.
*   **Region Scope**: Snapshot exists in Region where created. To use elsewhere -> **Copy Snapshot**.
*   **Stored in S3**: Snapshots are actually stored centrally in Amazon S3 (you don't see this bucket).
*   **Fast Snapshot Restore (FSR)**: Feature to create new volumes from snapshots extremely fast (avoids initial "lazy loading" latency).
*   **Recycle Bin**: Trash bin for Snapshots (keeps deleted snapshots for X days for recovery).

## 7. AMI (Amazon Machine Image)

*   Template to create EC2 Instances (contains OS, App, Config).
*   **Scope: REGION** (This is an exam trap).
    *   AMI created in Region A **cannot** start instance in Region B.
    *   **Solution**: Must use **Copy AMI** to Region B first.
*   **Sharing AMI**:
    *   Can share AMI with other accounts (questions about **Shared Services VPC** or **Golden Image**).
    *   **Note**: Cannot share AMI if created from Encrypted Snapshot (must share Key KMS + Snapshot + AMI).

## 8. Quick Comparison (Summary Battle)

| Criteria | EBS | Instance Store | EFS |
| :--- | :--- | :--- | :--- |
| **Scope** | 1 AZ | Physical Host (1 AZ) | Multi-AZ (Region) |
| **Speed** | Fast | Super Fast (Best) | Slower a bit |
| **Durability** | Durable | Lost on Stop | Very Durable |
| **Share** | 1 EC2 (except io1/2) | No | 1000s EC2s |
| **OS** | All | All | Linux Only |

---

<a id="vietnamese-version"></a>

# EC2 Storage (Instance Store, EBS, EFS)

## 1. EBS Volume Types (Các Loại Ổ Cứng) - Học thuộc lòng

EBS là ổ mạng (Network Drive), bị giới hạn trong **1 AZ**.

| Loại Volume | Tên mã | Specs (IOPS) - Cần nhớ | Keyword đề thi | Use Case (Dùng khi nào) |
| :--- | :--- | :--- | :--- | :--- |
| **General Purpose** | **gp3** (New), **gp2** | Max 16,000 IOPS. gp3: 3,000 IOPS free. gp2: 3 IOPS/GB (max 16k). | "Balance price/perf", "Boot volume", "System/Virtual desktop" | Mặc định cho hầu hết workload. **gp3** tách biệt config IOPS và Size. |
| **Provisioned IOPS** | **io1 / io2** | Max 64,000 (io1) / 256,000 (io2) IOPS. | "Mission-critical", "Sub-millisecond latency", "> 16,000 IOPS" | Database lớn (Oracle, SAP HANA, SQL Server) cần tốc độ vào/ra cực nhanh và ổn định. |
| **Throughput Opt HDD** | **st1** | Max 500 MB/s throughput. (IOPS thấp - 500). | "Big Data", "Data Warehouse", "Log processing", "Sequential I/O" | Xử lý dữ liệu lớn (Kafka, Splunk, Hadoop). **Không thể làm Boot Volume.** |
| **Cold HDD** | **sc1** | Max 250 MB/s throughput. (IOPS thấp - 250). | "Lowest cost", "Archive", "Infrequently accessed" | Lưu trữ dữ liệu ít dùng, File server giá rẻ. |

**Quy tắc vàng**: Chỉ có SSD (gp, io) mới được làm ổ Boot (Cài Win/Linux). HDD (st, sc) chỉ dùng làm ổ lưu dữ liệu.

## 2. EC2 Instance Store (Ephemeral Storage)

Đây là ổ cứng **vật lý** gắn trực tiếp vào máy chủ (Hardware attached).
*   **Tính chất**:
    *   **Tốc độ**: Khủng khiếp (nhanh hơn EBS nhiều vì không qua mạng).
    *   **Độ bền**: Kém. **Mất dữ liệu** nếu bạn Stop/Start máy (vì máy sẽ chuyển sang host vật lý khác).
*   **Keyword thi**: "High performance", "Temporary storage", "Cache", "Buffer", "Scratch data".
*   **Lưu ý**: Không dùng để lưu Database lâu dài (trừ khi có cơ chế replication như Cassandra/MongoDB).

## 3. Amazon EFS (Elastic File System)

Là ổ đĩa mạng chia sẻ (Network File System - NFS).
*   **Tính chất**:
    *   **Multi-AZ**: Dữ liệu tự động sao lưu ra nhiều AZ -> Rất an toàn.
    *   **Share**: Hàng nghìn EC2 có thể mount vào cùng lúc.
    *   **Elastic**: Tự động phình to/thu nhỏ dung lượng (Pay per use).
    *   **Linux Only**: Chỉ hỗ trợ Linux (POSIX), **không hỗ trợ Windows** (Windows phải dùng FSx).
*   **Performance Mode**:
    *   **General Purpose**: Mặc định (Web server, CMS).
    *   **Max I/O**: Big Data, song song hóa cao.

## 4. EBS Multi-Attach

*   Cho phép gắn 1 ổ EBS vào nhiều EC2 (cùng AZ).
*   Chỉ hỗ trợ: **io1, io2**.
*   **Use case**: Cluster application (ứng dụng tự quản lý đồng bộ ghi), Clustered Database.
*   **Lưu ý**: File system thường (ext4, xfs) không dùng được cái này, phải dùng Cluster-aware file system (như GFS2).

## 5. EBS Encryption (Mã Hoá)

*   Mã hóa toàn diện: Data at rest, Data in-flight, Snapshots đều được mã hóa.
*   **Minimal Impact**: Ảnh hưởng không đáng kể đến tốc độ (latency).
*   **Mẹo thi**: Làm sao để mã hóa một ổ cứng chưa mã hóa (Unencrypted)?
    1.  Tạo Snapshot của ổ cũ.
    2.  Copy Snapshot đó và tích vào ô "Encrypt".
    3.  Tạo ổ cứng mới từ Snapshot đã mã hóa.
    4.  Gắn ổ mới vào máy.

## 6. EBS Snapshots (Bản sao lưu) - Thi cực nhiều

*   **Incremental (Tăng trưởng)**: Chỉ lưu phần dữ liệu **thay đổi** so với lần trước -> Tiết kiệm tiền & thời gian.
*   **Region Scope**: Snapshot nằm ở Region nào thì chỉ thấy ở Region đó. Muốn dùng ở nơi khác phải **Copy Snapshot**.
*   **Lưu ở S3**: Thực chất Snapshot được lưu ngầm trong Amazon S3 (bạn không thấy bucket này).
*   **Fast Snapshot Restore (FSR)**: Tính năng giúp tạo volume mới từ snapshot cực nhanh (không bị latency lúc đầu do "lazy loading").
*   **Recycle Bin**: Thùng rác cho Snapshot (giữ lại snapshot đã xóa trong X ngày để lỡ tay xóa nhầm còn khôi phục được).

## 7. AMI (Amazon Machine Image)

*   Là bản mẫu để tạo ra EC2 Instances (chứa OS, App, Config).
*   **Phạm vi: REGION** (Đây là bẫy thi).
    *   AMI tạo ở Region A **không thể** dùng để bật máy ở Region B.
    *   **Giải pháp**: Phải dùng chức năng **Copy AMI** sang Region B trước.
*   **Chia sẻ AMI**:
    *   Có thể share AMI cho account khác dùng (câu hỏi về **Shared Services VPC** hay **Golden Image**).
    *   **Lưu ý**: Không share được AMI nếu nó được tạo từ Encrypted Snapshot (phải share cả Key KMS + Snapshot + AMI).

## 8. So Sánh Nhanh (Summary Battle)

| Tiêu chí | EBS | Instance Store | EFS |
| :--- | :--- | :--- | :--- |
| **Phạm vi** | 1 AZ | Physical Host (1 AZ) | Multi-AZ (Region) |
| **Tốc độ** | Nhanh | Siêu nhanh (Nhất) | Chậm hơn xíu |
| **Độ bền** | Bền | Mất khi Stop | Rất bền |
| **Chia sẻ** | 1 EC2 (trừ io1/2) | Không | 1000s EC2 |
| **Hệ điều hành** | All | All | Linux Only |
