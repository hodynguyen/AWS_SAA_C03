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
