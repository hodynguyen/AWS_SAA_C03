[Vietnamese Below](#vietnamese-version)

# AWS Storage Extras

## 1. AWS Snow Family Overview

The AWS Snow Family is a set of **highly-secure, portable physical devices** used to **collect and process data at the edge**, and/or **migrate data in and out of AWS** when network transfer is too slow or impractical.

### Why Snow Family?
*   Migrating **large amounts of data** over the network takes too long (e.g., 100TB over 1Gbps = ~12 days).
*   Network challenges: limited connectivity, limited bandwidth, high cost, shared bandwidth, unstable connection.
*   **Rule of thumb**: If it takes more than **1 week** to transfer data over the network → use Snow devices.

### Snow Family Devices

#### A. Snowcone & Snowcone SSD
*   **Smallest** device — small, portable, rugged, withstands harsh environments.
*   **Storage**: Snowcone = 8TB HDD | Snowcone SSD = 14TB SSD.
*   **Compute**: 2 CPUs, 4GB memory.
*   **Use Cases**: Edge computing, data collection in harsh/disconnected environments (desert, ocean, military).
*   **Data Transfer**: Can send back to AWS via shipping or **AWS DataSync** (over network).
*   **Power**: Can be powered by battery (optional).

#### B. Snowball Edge
*   **Large** physical data transport device — suitcase-sized.
*   Two variants:
    *   **Storage Optimized**: **80TB** HDD usable, 40 vCPUs, 80GB RAM. Best for large-scale data migration.
    *   **Compute Optimized**: **42TB** HDD/28TB NVMe, 104 vCPUs, 416GB RAM, optional GPU. Best for edge computing.
*   **Use Cases**: Large data migration (TB to PB), disaster recovery, edge computing.
*   Can run **EC2 instances** and **Lambda functions** locally (using AWS IoT Greengrass).

#### C. Snowmobile
*   An actual **truck** (45-foot shipping container) that can transfer **up to 100PB** of data.
*   Used for **exabyte-scale** data migration.
*   **Security**: GPS tracking, 24/7 video surveillance, escorted by security personnel.
*   Better than Snowball if you transfer **more than 10PB**.

### Snow Family Comparison

| Feature | Snowcone | Snowball Edge | Snowmobile |
|---|---|---|---|
| **Storage** | 8-14TB | 42-80TB | Up to 100PB |
| **Migration size** | Up to TBs | Up to PBs | Up to EBs |
| **Compute** | Basic (2 vCPU) | Powerful (40-104 vCPU) | N/A |
| **Transfer** | Shipping or DataSync | Shipping only | Shipping only |

### Edge Computing with Snow Family
*   Process data **at the edge** (locations with limited/no internet: mines, trucks, ships).
*   Run **EC2 instances** or **Lambda functions** directly on Snow devices.
*   All devices can run **EC2 Instances & AWS Lambda** (using AWS IoT Greengrass).
*   Long-term deployment: **1 to 3 years** discounted pricing.

### Snow Family into AWS (Data Flow)
1.  Request device from AWS Console.
2.  Install **snowball client** / **AWS OpsHub** on your server.
3.  Connect device and copy data.
4.  Ship device back to AWS.
5.  Data is loaded into **S3 bucket**.
6.  Snowball is completely **wiped** after import.

### OpsHub
*   A **GUI software** (installed on your computer) to manage Snow Family devices.
*   Replaces the old CLI-based management.
*   Can configure, transfer data, launch EC2 instances on Snow devices.

### Snowball into Glacier
*   **Cannot import directly** into Glacier.
*   Must import into **S3 first**, then use an **S3 Lifecycle Policy** to transition to Glacier.

### Exam Tips
*   Snow Family = **offline data migration** + **edge computing**.
*   > 1 week of network transfer → use **Snow devices**.
*   > 10PB → use **Snowmobile**.
*   Snowball **cannot import directly into Glacier** → S3 first, then lifecycle policy.
*   **OpsHub** = GUI tool to manage Snow devices.

## 2. Amazon FSx

Amazon FSx provides **fully managed, high-performance third-party file systems** on AWS. Instead of building your own file server, you launch a managed FSx file system.

### A. FSx for Windows File Server
*   Fully managed **Windows native** shared file system.
*   Built on **SMB protocol** and **Windows NTFS**.
*   Supports **Active Directory (AD)** integration, ACLs, user quotas.
*   Can be mounted on **Linux EC2 instances** as well.
*   Supports **Microsoft's Distributed File System (DFS) Namespaces** — group files across multiple FS.
*   **Performance**: Scales up to 10s of GB/s, millions of IOPS, 100s PB of data.
*   **Storage**: SSD (low-latency) or HDD (broad spectrum).
*   **Multi-AZ** for high availability.
*   Data is backed up daily to **S3**.

### B. FSx for Lustre
*   **Lustre** = Linux + Cluster — a high-performance **parallel distributed file system**.
*   Designed for **High Performance Computing (HPC)**.
*   Use Cases: Machine Learning, video processing, financial modeling, electronic design automation.
*   **Performance**: Scales up to 100s GB/s, millions of IOPS, sub-millisecond latencies.
*   **S3 Integration**: Can **read from S3** as a file system (lazy loading) and **write results back to S3**.
*   **Storage**: SSD (low-latency, IOPS intensive) or HDD (throughput intensive).
*   **Deployment Options**:
    *   **Scratch**: Temporary storage, no replication, high burst (6x faster). Use for short-term processing.
    *   **Persistent**: Long-term storage, data replicated within same AZ. Use for long-term sensitive data.

### C. FSx for NetApp ONTAP
*   Managed **NetApp ONTAP** file system on AWS.
*   Compatible with **NFS, SMB, iSCSI** protocols.
*   Works with **Linux, Windows, macOS, VMware Cloud on AWS**.
*   Features: Auto-scaling storage, snapshots, replication, compression, data deduplication, point-in-time cloning.
*   Great for **moving NAS workloads** to AWS.

### D. FSx for OpenZFS
*   Managed **OpenZFS** file system on AWS.
*   Compatible with **NFS** protocol.
*   Works with **Linux, Windows, macOS**.
*   **Performance**: Up to 1,000,000 IOPS, 0.5ms latency.
*   Features: Snapshots, compression, point-in-time cloning (helpful for testing).
*   Great for **moving ZFS workloads** to AWS.

### FSx Comparison

| Feature | Windows File Server | Lustre | NetApp ONTAP | OpenZFS |
|---|---|---|---|---|
| **Protocol** | SMB | Lustre | NFS, SMB, iSCSI | NFS |
| **OS Support** | Windows, Linux | Linux | All (Linux, Win, Mac) | All (Linux, Win, Mac) |
| **Best For** | Windows apps, AD | HPC, ML | NAS migration | ZFS migration |
| **S3 Integration** | No | **Yes** | No | No |
| **Multi-AZ** | Yes | No (Persistent: same AZ) | Yes | No |

### Exam Tips
*   **Windows File Server**: SMB protocol, Active Directory, Windows workloads.
*   **Lustre**: HPC, Machine Learning, S3 integration (Scratch = temp, Persistent = long-term).
*   **NetApp ONTAP**: Multi-protocol (NFS + SMB + iSCSI), NAS migration.
*   **OpenZFS**: NFS, ZFS migration, point-in-time cloning.
*   If you see "HPC" or "Machine Learning file system" → think **FSx for Lustre**.
*   If you see "Windows shared file system" or "Active Directory" → think **FSx for Windows**.

## 3. Storage Gateway Overview

AWS Storage Gateway is a **hybrid cloud storage service** that provides on-premises access to **virtually unlimited cloud storage**. It bridges your on-premises infrastructure with AWS cloud storage.

### Why Storage Gateway?
*   Companies want a **hybrid cloud** approach: some data on-premises, some in AWS.
*   Reasons: long cloud migrations, security requirements, compliance, IT strategy.
*   S3 is proprietary (not NFS/SMB), so you can't just mount it like a local drive → **Storage Gateway bridges this gap**.

### Gateway Types

#### A. S3 File Gateway
*   Configured S3 buckets accessible using **NFS** or **SMB** protocol.
*   Most recently used data is **cached locally** on the gateway for low-latency access.
*   Supports S3 Standard, S3 Standard-IA, S3 One Zone-IA, S3 Intelligent-Tiering.
*   Transition to **S3 Glacier** using Lifecycle Policies.
*   Access controlled by **IAM roles** for each File Gateway.
*   **SMB**: Integrated with **Active Directory** for user authentication.

#### B. FSx File Gateway
*   Provides access to **Amazon FSx for Windows File Server** from on-premises.
*   Local cache for **frequently accessed data**.
*   **Windows native** compatibility (SMB, NTFS, AD).
*   Use Case: Group file shares and home directories that need both on-prem and cloud access.

#### C. Volume Gateway
*   Block storage using **iSCSI** protocol, backed by S3.
*   Two types:
    *   **Cached Volumes**: Primary data in S3, frequently accessed data cached locally. Low-latency access to frequently used data.
    *   **Stored Volumes**: Entire dataset on-premises, scheduled backups (EBS Snapshots) to S3. Low-latency access to entire dataset.
*   Can create **EBS Snapshots** from volumes and restore as EBS volumes.

#### D. Tape Gateway
*   For companies using **physical tape backup** processes.
*   Virtual Tape Library (VTL) backed by **S3** and **Glacier**.
*   Back up data using existing **tape-based** backup software (Veeam, NetBackup, etc.).
*   Use Case: Replace physical tapes with cloud-backed virtual tapes.

### Hardware Appliance
*   If you don't have on-premises virtualization, AWS sells a **physical hardware appliance** you can install in your data center.
*   Works with all gateway types (File, Volume, Tape).
*   Helpful for **small data centers** with no virtual machine infrastructure.

### Exam Tips
*   Storage Gateway = **hybrid cloud storage** bridge between on-prem and AWS.
*   **S3 File Gateway**: NFS/SMB → S3 (with local cache).
*   **FSx File Gateway**: On-prem access to FSx for Windows.
*   **Volume Gateway**: iSCSI block storage → S3 (Cached or Stored). EBS Snapshots.
*   **Tape Gateway**: Virtual tapes → S3/Glacier (replace physical tapes).
*   If you see "on-premises to S3 with NFS" → **S3 File Gateway**.
*   If you see "backup tapes to cloud" → **Tape Gateway**.

---

<a id="vietnamese-version"></a>

# AWS Storage Extras

## 1. AWS Snow Family Overview (Tổng quan AWS Snow Family)

AWS Snow Family là tập hợp các **thiết bị vật lý di động, bảo mật cao** dùng để **thu thập và xử lý dữ liệu tại edge**, và/hoặc **di chuyển dữ liệu vào/ra AWS** khi truyền qua mạng quá chậm hoặc không khả thi.

### Tại sao cần Snow Family?
*   Di chuyển **lượng dữ liệu lớn** qua mạng tốn quá lâu (ví dụ: 100TB qua 1Gbps = ~12 ngày).
*   Thách thức mạng: kết nối hạn chế, băng thông thấp, chi phí cao, chia sẻ băng thông, kết nối không ổn định.
*   **Nguyên tắc**: Nếu mất hơn **1 tuần** để truyền dữ liệu qua mạng → dùng Snow devices.

### Các thiết bị Snow Family

#### A. Snowcone & Snowcone SSD
*   Thiết bị **nhỏ nhất** — nhỏ gọn, di động, chống chịu môi trường khắc nghiệt.
*   **Lưu trữ**: Snowcone = 8TB HDD | Snowcone SSD = 14TB SSD.
*   **Compute**: 2 CPUs, 4GB RAM.
*   **Use Cases**: Edge computing, thu thập dữ liệu ở môi trường khắc nghiệt/mất kết nối (sa mạc, đại dương, quân đội).
*   **Truyền dữ liệu**: Gửi về AWS bằng đường ship hoặc **AWS DataSync** (qua mạng).
*   **Nguồn điện**: Có thể dùng pin (tùy chọn).

#### B. Snowball Edge
*   Thiết bị vận chuyển dữ liệu **lớn** — cỡ vali.
*   Hai biến thể:
    *   **Storage Optimized**: **80TB** HDD, 40 vCPUs, 80GB RAM. Tốt nhất cho di chuyển dữ liệu lớn.
    *   **Compute Optimized**: **42TB** HDD/28TB NVMe, 104 vCPUs, 416GB RAM, GPU tùy chọn. Tốt nhất cho edge computing.
*   **Use Cases**: Di chuyển dữ liệu lớn (TB đến PB), disaster recovery, edge computing.
*   Có thể chạy **EC2 instances** và **Lambda functions** cục bộ (dùng AWS IoT Greengrass).

#### C. Snowmobile
*   Một **xe tải thực sự** (container dài 45 feet) có thể chuyển **tới 100PB** dữ liệu.
*   Dùng cho di chuyển dữ liệu cấp **exabyte**.
*   **Bảo mật**: Theo dõi GPS, camera 24/7, có đội bảo vệ đi kèm.
*   Tốt hơn Snowball nếu chuyển **hơn 10PB**.

### So sánh Snow Family

| Đặc điểm | Snowcone | Snowball Edge | Snowmobile |
|---|---|---|---|
| **Lưu trữ** | 8-14TB | 42-80TB | Tới 100PB |
| **Quy mô** | Tới TBs | Tới PBs | Tới EBs |
| **Compute** | Cơ bản (2 vCPU) | Mạnh (40-104 vCPU) | Không có |
| **Truyền** | Ship hoặc DataSync | Chỉ ship | Chỉ ship |

### Edge Computing với Snow Family
*   Xử lý dữ liệu **tại edge** (nơi internet hạn chế/không có: mỏ quặng, xe tải, tàu biển).
*   Chạy **EC2 instances** hoặc **Lambda functions** trực tiếp trên Snow devices.
*   Tất cả thiết bị có thể chạy **EC2 & Lambda** (dùng AWS IoT Greengrass).
*   Triển khai dài hạn: giá giảm cho hợp đồng **1 đến 3 năm**.

### Luồng dữ liệu Snow Family → AWS
1.  Request thiết bị từ AWS Console.
2.  Cài **snowball client** / **AWS OpsHub** trên server.
3.  Kết nối thiết bị và copy dữ liệu.
4.  Ship thiết bị về AWS.
5.  Dữ liệu được load vào **S3 bucket**.
6.  Snowball được **xóa hoàn toàn** sau khi import.

### OpsHub
*   **Phần mềm GUI** (cài trên máy bạn) để quản lý Snow Family devices.
*   Thay thế quản lý bằng CLI cũ.
*   Có thể cấu hình, truyền dữ liệu, chạy EC2 instances trên Snow devices.

### Snowball vào Glacier
*   **Không thể import trực tiếp** vào Glacier.
*   Phải import vào **S3 trước**, rồi dùng **S3 Lifecycle Policy** để chuyển sang Glacier.

### Exam Tips
*   Snow Family = **di chuyển dữ liệu offline** + **edge computing**.
*   > 1 tuần truyền qua mạng → dùng **Snow devices**.
*   > 10PB → dùng **Snowmobile**.
*   Snowball **không import trực tiếp vào Glacier** → S3 trước, rồi lifecycle policy.
*   **OpsHub** = công cụ GUI để quản lý Snow devices.

## 2. Amazon FSx

Amazon FSx cung cấp **hệ thống file bên thứ 3 hiệu suất cao, được quản lý hoàn toàn** trên AWS. Thay vì tự dựng file server, bạn chỉ cần khởi chạy FSx.

### A. FSx for Windows File Server
*   Hệ thống file **Windows native** được quản lý hoàn toàn.
*   Dựa trên giao thức **SMB** và **Windows NTFS**.
*   Hỗ trợ tích hợp **Active Directory (AD)**, ACLs, user quotas.
*   Có thể mount trên cả **Linux EC2 instances**.
*   Hỗ trợ **Microsoft DFS Namespaces** — gộp file từ nhiều file system.
*   **Hiệu suất**: Lên tới hàng chục GB/s, hàng triệu IOPS, hàng trăm PB dữ liệu.
*   **Lưu trữ**: SSD (độ trễ thấp) hoặc HDD (đa dụng).
*   **Multi-AZ** cho tính sẵn sàng cao.
*   Dữ liệu được backup hàng ngày vào **S3**.

### B. FSx for Lustre
*   **Lustre** = Linux + Cluster — hệ thống file **phân tán song song** hiệu suất cao.
*   Thiết kế cho **High Performance Computing (HPC)**.
*   Use Cases: Machine Learning, xử lý video, mô hình tài chính, thiết kế điện tử.
*   **Hiệu suất**: Lên tới 100s GB/s, hàng triệu IOPS, độ trễ dưới mili giây.
*   **Tích hợp S3**: Có thể **đọc từ S3** như file system (lazy loading) và **ghi kết quả về S3**.
*   **Lưu trữ**: SSD (độ trễ thấp, IOPS cao) hoặc HDD (throughput cao).
*   **Deployment Options**:
    *   **Scratch**: Lưu trữ tạm, không replicate, burst nhanh (6x). Dùng cho xử lý ngắn hạn.
    *   **Persistent**: Lưu trữ dài hạn, dữ liệu replicate trong cùng AZ. Dùng cho dữ liệu nhạy cảm.

### C. FSx for NetApp ONTAP
*   Hệ thống file **NetApp ONTAP** được quản lý trên AWS.
*   Tương thích **NFS, SMB, iSCSI**.
*   Hoạt động với **Linux, Windows, macOS, VMware Cloud on AWS**.
*   Tính năng: Auto-scaling storage, snapshots, replication, nén, data deduplication, point-in-time cloning.
*   Tuyệt vời để **chuyển NAS workloads** lên AWS.

### D. FSx for OpenZFS
*   Hệ thống file **OpenZFS** được quản lý trên AWS.
*   Tương thích giao thức **NFS**.
*   Hoạt động với **Linux, Windows, macOS**.
*   **Hiệu suất**: Lên tới 1,000,000 IOPS, độ trễ 0.5ms.
*   Tính năng: Snapshots, nén, point-in-time cloning (hữu ích cho testing).
*   Tuyệt vời để **chuyển ZFS workloads** lên AWS.

### So sánh FSx

| Đặc điểm | Windows File Server | Lustre | NetApp ONTAP | OpenZFS |
|---|---|---|---|---|
| **Giao thức** | SMB | Lustre | NFS, SMB, iSCSI | NFS |
| **OS** | Windows, Linux | Linux | Tất cả | Tất cả |
| **Tốt cho** | Windows apps, AD | HPC, ML | NAS migration | ZFS migration |
| **Tích hợp S3** | Không | **Có** | Không | Không |
| **Multi-AZ** | Có | Không (Persistent: cùng AZ) | Có | Không |

### Exam Tips
*   **Windows File Server**: SMB, Active Directory, Windows workloads.
*   **Lustre**: HPC, Machine Learning, tích hợp S3 (Scratch = tạm, Persistent = dài hạn).
*   **NetApp ONTAP**: Đa giao thức (NFS + SMB + iSCSI), NAS migration.
*   **OpenZFS**: NFS, ZFS migration, point-in-time cloning.
*   Thấy "HPC" hoặc "Machine Learning file system" → nghĩ đến **FSx for Lustre**.
*   Thấy "Windows shared file system" hoặc "Active Directory" → nghĩ đến **FSx for Windows**.

## 3. Storage Gateway Overview (Tổng quan Storage Gateway)

AWS Storage Gateway là dịch vụ **lưu trữ hybrid cloud** cung cấp truy cập từ on-premises vào **lưu trữ cloud gần như không giới hạn**. Nó kết nối hạ tầng on-premises với AWS cloud storage.

### Tại sao cần Storage Gateway?
*   Công ty muốn **hybrid cloud**: một phần dữ liệu on-premises, một phần trên AWS.
*   Lý do: di chuyển cloud dài hạn, yêu cầu bảo mật, compliance, chiến lược IT.
*   S3 là proprietary (không phải NFS/SMB), không thể mount như ổ đĩa cục bộ → **Storage Gateway là cầu nối**.

### Các loại Gateway

#### A. S3 File Gateway
*   S3 buckets truy cập qua giao thức **NFS** hoặc **SMB**.
*   Dữ liệu hay dùng gần đây được **cache cục bộ** trên gateway.
*   Hỗ trợ S3 Standard, S3 Standard-IA, S3 One Zone-IA, S3 Intelligent-Tiering.
*   Chuyển sang **S3 Glacier** bằng Lifecycle Policies.
*   Quyền truy cập qua **IAM roles** cho mỗi File Gateway.
*   **SMB**: Tích hợp với **Active Directory** để xác thực.

#### B. FSx File Gateway
*   Cung cấp truy cập **Amazon FSx for Windows File Server** từ on-premises.
*   Cache cục bộ cho **dữ liệu hay truy cập**.
*   Tương thích **Windows native** (SMB, NTFS, AD).
*   Use Case: Chia sẻ file và thư mục home cần truy cập cả on-prem và cloud.

#### C. Volume Gateway
*   Lưu trữ block dùng giao thức **iSCSI**, backed bởi S3.
*   Hai loại:
    *   **Cached Volumes**: Dữ liệu chính trên S3, dữ liệu hay dùng cache cục bộ.
    *   **Stored Volumes**: Toàn bộ dữ liệu on-premises, backup định kỳ (EBS Snapshots) lên S3.
*   Có thể tạo **EBS Snapshots** từ volumes và restore thành EBS volumes.

#### D. Tape Gateway
*   Dành cho công ty dùng **backup băng từ vật lý**.
*   Virtual Tape Library (VTL) backed bởi **S3** và **Glacier**.
*   Backup bằng phần mềm **tape-based** sẵn có (Veeam, NetBackup, v.v.).
*   Use Case: Thay thế băng từ vật lý bằng băng từ ảo trên cloud.

### Hardware Appliance
*   Nếu không có hạ tầng ảo hóa, AWS bán **thiết bị phần cứng vật lý** cài đặt trong data center của bạn.
*   Tương thích với tất cả gateway types (File, Volume, Tape).
*   Phù hợp cho **data center nhỏ** không có hạ tầng máy ảo.

### Exam Tips
*   Storage Gateway = **hybrid cloud storage** kết nối on-prem và AWS.
*   **S3 File Gateway**: NFS/SMB → S3 (có local cache).
*   **FSx File Gateway**: Truy cập FSx for Windows từ on-prem.
*   **Volume Gateway**: iSCSI block storage → S3 (Cached hoặc Stored). EBS Snapshots.
*   **Tape Gateway**: Băng từ ảo → S3/Glacier (thay thế băng vật lý).
*   Thấy "on-premises to S3 with NFS" → **S3 File Gateway**.
*   Thấy "backup tapes to cloud" → **Tape Gateway**.
