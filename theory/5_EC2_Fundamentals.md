[Vietnamese Below](#vietnamese-version)

# EC2 Fundamentals

EC2 (Elastic Compute Cloud) is an IaaS service. Below are the "critical" points to remember for the exam.

## 1. Instance Purchasing Options (Extremely Important)

The exam will have scenarios like: "Company wants to save money, workload characteristics are... which option to choose?"

| Instance Type | "Keyword" Characteristics in Exam | Use Case | Discount Level |
| :--- | :--- | :--- | :--- |
| **On-Demand** | "Short-term", "Unpredictable", "No upfront" | Short-term workload, spiky, unpredictable. | Most Expensive (List Price) |
| **Reserved Instances (RI)** | "Steady state", "Long-term", "1-3 years" | Database, Backend running 24/7. Commitment of 1 or 3 years. | ~72% discount |
| **Convertible RI** | "Change capability", "Flexible" | Like RI but **allowed to change instance type** later (e.g., C5 -> R5). | ~54% discount |
| **Spot Instances** | "Stateless", "Fault-tolerant", "Can fail", "Cheapest" | Image processing jobs, Batch processing, CI/CD. **Can be reclaimed by AWS with a 2-minute notice.** | Cheapest (Up to 90% discount) |
| **Dedicated Hosts** | "Compliance", "License BYOL", "Physical server" | Need hardware compliance or use existing software licenses (BYOL - per socket/core). | Most expensive in the solar system |
| **Dedicated Instances** | "Hardware isolation" | Just ensuring no shared hardware with other customers (but no control over sockets like Hosts). | Second most expensive |
| **Savings Plans** | "Flexible (Compute)", "Long-term commitment" | Newer and more flexible than RI. <br> **Compute SP**: Applies to EC2, Fargate, Lambda (regardless of Region/Instance Family). <br> **EC2 Instance SP**: Specific to 1 Family in 1 Region (like RI). | ~66-72% discount |
| **Capacity Reservations** | "Reserve capacity", "Specific AZ" | Only to **reserve capacity** for you (ensures machines are available when needed). Usually combined with RI/Savings Plans for discounts (as it is charged at On-Demand rates by itself). | No discount (Reservation only) |

### Spot Fleet
A collection of multiple Spot Instances + (optional) On-Demand instances. Automatically replaces instances when reclaimed.
* **Strategies** (Exam often asks):
    * **lowestPrice**: Buy the cheapest -> Most savings, but high risk of "sweep" if prices rise.
    * **diversified**: Buy scattered across types (e.g., c5.large, m5.large) -> Most stable (High Availability), if one dies the other survives.
    * **capacityOptimized**: Choose the one with the most "spare" capacity -> Lowest risk of reclamation.

## 2. Security Groups (SG) - Soft Firewall

* **Scope**: Operates at the **Instance** level.
* **Stateful**:
    * If you allow inbound (Inbound Allow) -> Outbound is **Automatically allowed** (even if outbound rules deny).
* **Rules**:
    * Only **ALLOW**, no DENY. (To deny specific IPs, use **NACL**).
    * Default: Block all inbound, Allow all outbound.
* **Reference**: SG can reference another SG. (e.g., SG-Web allows access from SG-LoadBalancer).

## 3. Important Ports

Must memorize to know which doors the Security Group is opening:
* **22**: SSH (Linux) / SFTP.
* **3389**: RDP (Remote Desktop for Windows).
* **80**: HTTP.
* **443**: HTTPS.

## 4. EC2 User Data

* A script that runs **only once** when the machine first boots (Bootstrapping).
* Runs with **Root** privileges (sudo).
* Used for: OS updates, installing Docker, downloading Git repos, starting services immediately upon boot.

## 5. Instance Types (Instance Families)

Mnemonic: "Name implies function".
* **R** (RAM): Memory Optimized -> Database (In-memory DB like Redis), Cache.
* **C** (Compute): Compute Optimized -> Heavy data processing, Batch processing, Media Transcoding, Gaming servers.
* **I** (I/O): Storage Optimized -> Data Warehouse, Database needing extremely high IOPS.
* **G** (Graphics): GPU Optimized -> Machine Learning, Video Rendering.
* **T** (General/Burstable): Cheap line, accumulates CPU Credits (T2/T3) -> Small Web servers, Dev environments.

## 6. SSH & Key Pairs

* **Private Key (.pem)**: Keep secret on your machine. If lost, you cannot access EC2 again.
* **Public Key**: AWS keeps it.
* **Common Error**: "Unprotected Private Key File" (Permission denied) -> Need to run `chmod 400 key.pem` (on Mac/Linux) to protect the key file.
* **EC2 Instance Connect**: New way to SSH via browser (Browser-based), no need to manage complex .pem key files, but only supports Linux.

---

<a id="vietnamese-version"></a>

# EC2 Fundamentals

EC2 (Elastic Compute Cloud) là dịch vụ IaaS. Dưới đây là những điểm "chết người" cần nhớ để đi thi.

## 1. Instance Purchasing Options (Các Gói Mua - Cực kì Quan Trọng)

Đi thi sẽ có dạng bài toán: "Công ty muốn tiết kiệm tiền, đặc điểm workload như này... chọn gói nào?"

| Loại Instance | Đặc điểm "Keyword" trong đề | Use Case (Trường hợp dùng) | Mức giảm giá |
| :--- | :--- | :--- | :--- |
| **On-Demand** | "Short-term", "Unpredictable", "No upfront" | Workload ngắn hạn, spiky, không đoán trước được. | Đắt nhất (Giá gốc) |
| **Reserved Instances (RI)** | "Steady state", "Long-term", "1-3 years" | Database, Backend chạy 24/7. Cam kết mua 1 hoặc 3 năm. | Giảm ~72% |
| **Convertible RI** | "Change capability", "Flexible" | Giống RI nhưng **được phép đổi loại instance** sau này (VD: C5 -> R5). | Giảm ~54% |
| **Spot Instances** | "Stateless", "Fault-tolerant", "Can fail", "Cheapest" | Job xử lý ảnh, Batch processing, CI/CD. **Có thể bị AWS thu hồi với notice 2 phút.** | Rẻ nhất (Giảm tới 90%) |
| **Dedicated Hosts** | "Compliance", "License BYOL", "Physical server" | Cần sát hạch phần cứng (Compliance) hoặc dùng License phần mềm cũ (tính theo socket/core). | Đắt nhất hệ mặt trời |
| **Dedicated Instances** | "Hardware isolation" | Chỉ cần không dùng chung phần cứng với khách hàng khác (nhưng không được control socket như Host). | Đắt nhì |
| **Savings Plans** | "Flexible (Compute)", "Long-term commitment" | Mới và linh hoạt hơn RI. <br> **Compute SP**: Apply cho cả EC2, Fargate, Lambda (bất kể Region/Instance Family). <br> **EC2 Instance SP**: Cụ thể cho 1 Family tại 1 Region (giống RI). | Giảm ~66-72% |
| **Capacity Reservations** | "Reserve capacity", "Specific AZ" | Chỉ để **giữ chỗ** cho bạn (đảm bảo khi cần bật máy là có ngay, không sợ hết hàng). Thường đi kèm với RI/Savings Plans để được giảm giá (vì bản thân nó tính giá On-Demand). | Không giảm giá (Chỉ giữ chỗ) |

### Spot Fleet (Đội hình Spot)
Là tập hợp nhiều Spot Instances + (tùy chọn) On-Demand. Tự động thay thế instance khi bị thu hồi.
* **Strategies (Chiến thuật)** - Thi hay hỏi:
    * **lowestPrice**: Mua con rẻ nhất -> Tiết kiệm nhất, nhưng rủi ro bị "quét sạch" nếu giá tăng.
    * **diversified**: Mua rải rác nhiều loại (VD: c5.large, m5.large) -> Ổn định nhất (High Availability), con này chết còn con kia.
    * **capacityOptimized**: Chọn con nào đang "ế" nhất (dư thừa nhiều nhất) -> Ít rủi ro bị thu hồi nhất.

## 2. Security Groups (SG) - Firewall Mềm

* **Phạm vi**: Hoạt động ở cấp độ **Instance**.
* **Stateful (Có trạng thái)**:
    * Nếu bạn cho phép chiều vào (Inbound Allow) -> Chiều ra (Outbound) **Tự động cho phép** (dù rule outbound có cấm).
* **Rules**:
    * Chỉ có **ALLOW** (Cho phép), không có DENY. (Muốn cấm IP cụ thể thì phải dùng **NACL**).
    * Mặc định: Chặn tất cả inbound, Cho phép tất cả outbound.
* **Tham chiếu**: SG có thể reference một SG khác. (VD: SG-Web cho phép SG-LoadBalancer truy cập).

## 3. Các Port Quan Trọng

Phải thuộc lòng để biết Security Group đang mở cửa nào:
* **22**: SSH (LInux) / SFTP.
* **3389**: RDP (Remote Desktop cho Windows).
* **80**: HTTP.
* **443**: HTTPS.

## 4. EC2 User Data

* Là script chạy **duy nhất 1 lần** đầu tiên khi máy khởi động (Bootstrapping).
* Chạy với quyền **Root** (sudo).
* Dùng để: Cập nhật OS, cài Docker, tải Git repo, start service ngay khi máy bật lên.

## 5. Instance Types (Các họ máy)

Mẹo nhớ: "Món nào tên nấy".
* **R** (RAM): Memory Optimized -> Database (In-memory DB like Redis), Cache.
* **C** (Compute): Compute Optimized -> Xử lý data nặng, Batch processing, Media Transcoding, Gaming server.
* **I** (I/O): Storage Optimized -> Data Warehouse, Database cần IOPS cực cao.
* **G** (Graphics): GPU Optimized -> Machine Learning, Video Rendering.
* **T** (General/Burstable): Dòng giá rẻ, tích điểm CPU Credits (T2/T3) -> Web server nhỏ, Dev enviroment.

## 6. SSH & Key Pairs

* **Private Key (.pem)**: Giữ bí mật trên máy bạn. Mất là khỏi vào lại EC2.
* **Public Key**: AWS giữ.
* **Lỗi thường gặp**: "Unprotected Private Key File" (Permission denied) -> Cần chạy lệnh `chmod 400 key.pem` (trên Mac/Linux) để bảo vệ file key.
* **EC2 Instance Connect**: Cách mới để SSH qua trình duyệt (Browser-based), không cần lo quản lý file key .pem phức tạp, nhưng chỉ hỗ trợ Linux.
