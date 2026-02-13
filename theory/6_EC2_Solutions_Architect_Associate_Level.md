[Vietnamese Below](#vietnamese-version)

# EC2 Solutions Architect Associate Level

## 1. Public vs Private vs Elastic IP

| IP Type | Characteristics | When to use? |
| :--- | :--- | :--- |
| **Private IP** | Used only within AWS internal network (VPC). Retained after reboot. | Communication between Web Server and DB Server. |
| **Public IP** | Public IP to access the Internet. **Changes** after every Stop/Start instance. | Web Servers needing internet access but not a fixed IP. |
| **Elastic IP (EIP)** | **FIXED** Public IP (Static IPv4). Does not change on Stop/Start. | When firewall IP whitelisting is needed, or attached to critical Servers. **Note**: Max 5 EIPs/Region. Better to use Load Balancer instead of EIP. |

**Exam Tip (Cost)**: EIP is free IF attached to a **RUNNING** instance. If you request an EIP but **do not use it** (or attach it to a stopped instance) -> **AWS will charge a penalty** (to avoid wasting public resources).

## 2. EC2 Placement Groups (Placement Strategy) - Highly Tested

How do you want to physically place your EC2 instances?

### a) Cluster
* **Description**: Pack all instances into **one Rack**, same **single AZ**.
* **Pros**: Extremely low latency (lowest), Extremely high network speed (10Gbps+).
* **Cons**: High risk. If that Rack fails -> The whole cluster dies.
* **Use case**: Big Data, super-fast computing, HPC, ML training requiring fast network.

### b) Spread
* **Description**: Place each instance on completely distinct hardware (Rack).
* **Limit**: Max **7 instances / AZ**.
* **Pros**: Safest (High Availability). If one Rack burns, others survive.
* **Use case**: Critical Applications, small important systems (not for Big Data).

### c) Partition
* **Description**: Divide instances into logical groups (Partitions). Instances in one partition do not share a rack with another partition.
* **Limit**: Max **7 partitions / AZ** (but each partition can contain multiple instances).
* **Use case**: Large distributed systems like **Hadoop, Cassandra, Kafka** (HDFS needs to know which servers share a rack for data backup).

## 3. Elastic Network Interfaces (ENI)

AWS "Virtual Network Card".
* **Primary ENI (eth0)**: Attached to instance at creation. **Cannot be detached**.
* **Secondary ENI (eth1, eth2...)**: Can be detached and attached to another machine (Hot attach) even while the machine is running.
* **Scope**: Limited within **AZ** (ENI in AZ A cannot be attached to EC2 in AZ B).
* **Use case**:
    * Create separate Management Network.
    * Low-cost Failover (Machine A dies, move ENI to Machine B to keep Private IP).

## 4. EC2 Hibernate (Hibernation Mode)

* **Normal (Stop)**: Clears RAM, shuts down CPU. Rebooting starts from scratch (slow).
* **Hibernate**:
    * Saves all data in **RAM** to **EBS Root Volume** (like hibernate file in Windows).
    * Shuts down machine.
    * On resume: Loads file from EBS to RAM -> Computer returns to previous state extremely fast.
* **Requirements**:
    * EBS Root Volume must be **Encrypted**.
    * RAM instance < 150 GB.
    * Does not support Bare Metal instances.
* **Use case**: Applications with very long startup times (loading cache takes > 15 mins), need to be usable immediately upon waking.

---

<a id="vietnamese-version"></a>

# EC2 Solutions Architect Associate Level

## 1. Public vs Private vs Elastic IP

| Loại IP | Đặc điểm | Khi nào dùng? |
| :--- | :--- | :--- |
| **Private IP** | Chỉ dùng trong nội bộ mạng AWS (VPC). Khởi động lại máy vẫn giữ nguyên. | Giao tiếp giữa Web Server và DB Server. |
| **Public IP** | IP công cộng để ra Internet. **Thay đổi** sau mỗi lần Stop/Start instance. | Dùng cho Web Server cần ra net nhưng không quan trọng IP cố định. |
| **Elastic IP (EIP)** | IP công cộng **CỐ ĐỊNH** (Static IPv4). Không đổi khi Stop/Start. | Khi cần whitelist firewall IP, hoặc gắn vào Server quan trọng. **Lưu ý**: Tối đa 5 EIP/Region. Nên dùng Load Balancer thay vì EIP. |

**Mẹo thi (Cost)**: EIP là miễn phí NẾU nó đang gắn vào 1 instance **ĐANG CHẠY**. Nếu bạn xin EIP mà **không dùng** (hoặc gắn vào máy đang tắt) -> **AWS sẽ tính tiền phạt** (để tránh lãng phí tài nguyên công cộng).

## 2. EC2 Placement Groups (Chiến lược đặt vị trí) - Thi cực nhiều

Bạn muốn sắp xếp các máy EC2 của mình như thế nào về mặt vật lý?

### a) Cluster (Cụm)
* **Mô tả**: Gom tất cả instance vào cùng **một Rack**, cùng **một AZ**.
* **Ưu điểm**: Latency cực thấp (thấp nhất), Tốc độ mạng cực cao (10Gbps+).
* **Nhược điểm**: Rủi ro cao. Nếu cái Rack đó hỏng -> Chết cả cụm.
* **Use case**: Big Data, tính toán siêu nhanh, HPC, ML training cần mạng nhanh.

### b) Spread (Phân tán)
* **Mô tả**: Đặt mỗi instance ở một phần cứng (Rack) khác nhau hoàn toàn.
* **Giới hạn**: Tối đa **7 instances / AZ**.
* **Ưu điểm**: An toàn nhất (High Availability). Rack này cháy Rack kia vẫn sống.
* **Use case**: Critical Application, các hệ thống nhỏ quan trọng (không dùng cho Big Data).

### c) Partition (Phân vùng)
* **Mô tả**: Chia instances thành các nhóm logic (Partitions). Instances trong partition này không chung rack với partition kia.
* **Giới hạn**: Tối đa **7 partitions / AZ** (nhưng mỗi partition chứa được nhiều instances).
* **Use case**: Hệ thống phân tán lớn như **Hadoop, Cassandra, Kafka** (HDFS cần biết server nào chung rack để backup data).

## 3. Elastic Network Interfaces (ENI)

Là "Card mạng ảo" của AWS.
* **Primary ENI (eth0)**: Gắn chết với instance lúc tạo. **Không thể tháo rời**.
* **Secondary ENI (eth1, eth2...)**: Có thể tháo ra gắn vào máy khác (Hot attach) ngay cả khi máy đang chạy.
* **Phạm vi**: Bị giới hạn trong **AZ** (ENI ở AZ A không thể gắn cho EC2 ở AZ B).
* **Use case**:
    * Tạo mạng quản trị riêng (Management Network).
    * Failover giá rẻ (Máy A chết, tháo ENI gắn sang máy B để giữ nguyên Private IP).

## 4. EC2 Hibernate (Chế độ ngủ đông)

* **Bình thường (Stop)**: Xóa RAM, tắt CPU. Khi bật lại boot từ đầu (lâu).
* **Hibernate**:
    * Lưu toàn bộ dữ liệu trong **RAM** xuống ổ cứng **EBS Root Volume** (như file hibernate trong Windows).
    * Tắt máy.
    * Khi bật lại: Load file từ EBS lên RAM -> Máy tính trở lại trạng thái cũ cực nhanh.
* **Yêu cầu**:
    * EBS Root Volume phải được **Encrypt (Mã hóa)**.
    * RAM instance < 150 GB.
    * Không hỗ trợ Bare Metal instances.
* **Use case**: Các ứng dụng khởi động quá lâu (load cache mất 15 phút), cần bật lên là dùng được ngay.
