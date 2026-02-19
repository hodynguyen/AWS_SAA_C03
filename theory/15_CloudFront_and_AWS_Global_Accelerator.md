[Vietnamese Below](#vietnamese-version)

# CloudFront & AWS Global Accelerator

## 1. CloudFront Overview

Amazon CloudFront is a **Content Delivery Network (CDN)** service that distributes your content to users with **low latency** and **high transfer speeds** by caching content at **Edge Locations** worldwide.

### How It Works
*   Content is cached at **216+ Edge Locations** (Points of Presence) globally.
*   When a user requests content, it's served from the **nearest Edge Location** instead of the origin server.
*   If the content is not in the cache (**cache miss**), CloudFront fetches it from the **origin**, caches it, and serves it to the user.
*   Subsequent requests are served directly from the cache (**cache hit**) — much faster.

### Origins
CloudFront can pull content from several types of origins:

#### A. S3 Bucket
*   Distribute and cache files (images, videos, static assets) at the edge.
*   Enhanced security with **Origin Access Control (OAC)** — ensures the S3 bucket is only accessible through CloudFront (replaces legacy Origin Access Identity - OAI).
*   CloudFront can also be used as an **ingress** — to upload files to S3.

#### B. Custom Origin (HTTP)
*   **Application Load Balancer (ALB)** — ALB must be **public**, EC2 instances behind it can be private.
*   **EC2 Instance** — must be **public** (or behind a public ALB). Security Group must allow Edge Location IPs.
*   **S3 Website** — S3 bucket configured as a static website.
*   **Any HTTP backend** — your own on-premises server or any HTTP endpoint.

### CloudFront vs S3 Cross Region Replication

| Feature | CloudFront | S3 Cross Region Replication |
|---|---|---|
| **Network** | 216+ Edge Locations globally | Must be set up per region |
| **Caching** | Cached for a TTL (Time to Live) | No caching, real-time sync |
| **Content** | Great for **static content** that must be available **everywhere** | Great for **dynamic content** that needs low-latency in **few regions** |
| **Read/Write** | Read-only cache | Read-write replication |
| **Update speed** | Files updated after TTL expires | Near real-time replication |

### Exam Tips
*   CloudFront = **CDN** = cache content at edge locations for low latency.
*   **OAC (Origin Access Control)** is the modern way to restrict S3 access to CloudFront only.
*   ALB origin must be **public**; EC2 origin must be **public** or behind public ALB.
*   Use CloudFront for **static, globally distributed** content; S3 CRR for **dynamic, region-specific** content.

## 2. CloudFront - ALB/EC2 as an Origin

CloudFront can use **EC2 instances** or **Application Load Balancers (ALB)** as origins for dynamic content.

### A. EC2 Instance as Origin
*   EC2 instances must be **public** (have a public IP).
*   **Security Group** of EC2 must allow inbound traffic from **CloudFront Edge Locations' public IPs**.
    *   AWS publishes the list of Edge Location IPs — you must allow all of them.
*   Flow: `Users → Edge Locations → (Public Internet) → EC2 Instance`.

### B. ALB as Origin
*   ALB must be **public** (internet-facing).
*   EC2 instances behind the ALB can be **private** (no public IP needed).
*   **Security Group of ALB** must allow inbound from **CloudFront Edge Locations' public IPs**.
*   **Security Group of EC2** only needs to allow traffic from the **ALB's Security Group**.
*   Flow: `Users → Edge Locations → (Public Internet) → ALB (public) → EC2 (private)`.

### Key Differences

| Aspect | EC2 as Origin | ALB as Origin |
|---|---|---|
| **EC2 visibility** | Must be **public** | Can be **private** |
| **Security Group** | Must allow all Edge Location IPs | ALB allows Edge IPs; EC2 allows ALB SG only |
| **Scalability** | Single instance | Load balanced across multiple instances |
| **Recommended** | Simple use cases | Production workloads |

### Exam Tips
*   EC2 as origin → EC2 must be **public**, SG allows Edge Location IPs.
*   ALB as origin → ALB must be **public**, EC2 behind it can be **private**.
*   ALB approach is **more secure** — EC2 instances don't need public IPs.

---

<a id="vietnamese-version"></a>

# CloudFront & AWS Global Accelerator

## 1. CloudFront Overview (Tổng quan CloudFront)

Amazon CloudFront là dịch vụ **Content Delivery Network (CDN)** phân phối nội dung đến người dùng với **độ trễ thấp** và **tốc độ truyền tải cao** bằng cách cache nội dung tại các **Edge Locations** trên toàn thế giới.

### Cách hoạt động
*   Nội dung được cache tại **216+ Edge Locations** (Điểm hiện diện) trên toàn cầu.
*   Khi người dùng request nội dung, nó được phục vụ từ **Edge Location gần nhất** thay vì server gốc.
*   Nếu nội dung chưa có trong cache (**cache miss**), CloudFront lấy từ **origin**, cache lại, rồi phục vụ cho người dùng.
*   Các request tiếp theo được phục vụ trực tiếp từ cache (**cache hit**) — nhanh hơn rất nhiều.

### Origins (Nguồn)
CloudFront có thể lấy nội dung từ nhiều loại origin:

#### A. S3 Bucket
*   Phân phối và cache file (ảnh, video, tài nguyên tĩnh) tại edge.
*   Bảo mật tốt hơn với **Origin Access Control (OAC)** — đảm bảo S3 bucket chỉ được truy cập qua CloudFront (thay thế Origin Access Identity - OAI cũ).
*   CloudFront cũng có thể dùng làm **ingress** — để upload file lên S3.

#### B. Custom Origin (HTTP)
*   **Application Load Balancer (ALB)** — ALB phải **public**, EC2 instances phía sau có thể private.
*   **EC2 Instance** — phải **public** (hoặc đặt sau ALB public). Security Group phải cho phép IP của Edge Locations.
*   **S3 Website** — S3 bucket được cấu hình làm web tĩnh.
*   **Bất kỳ HTTP backend nào** — server on-premises hoặc bất kỳ HTTP endpoint nào.

### CloudFront vs S3 Cross Region Replication

| Đặc điểm | CloudFront | S3 Cross Region Replication |
|---|---|---|
| **Mạng** | 216+ Edge Locations toàn cầu | Phải thiết lập từng region |
| **Cache** | Cache theo TTL (Time to Live) | Không cache, đồng bộ thời gian thực |
| **Nội dung** | Tốt cho **nội dung tĩnh** cần có mặt **khắp nơi** | Tốt cho **nội dung động** cần độ trễ thấp ở **vài region** |
| **Đọc/Ghi** | Cache chỉ đọc | Sao chép đọc-ghi |
| **Tốc độ cập nhật** | File cập nhật sau khi TTL hết hạn | Sao chép gần thời gian thực |

### Exam Tips
*   CloudFront = **CDN** = cache nội dung tại edge locations để giảm độ trễ.
*   **OAC (Origin Access Control)** là cách hiện đại để giới hạn truy cập S3 chỉ qua CloudFront.
*   ALB origin phải **public**; EC2 origin phải **public** hoặc đặt sau ALB public.
*   Dùng CloudFront cho **nội dung tĩnh, phân phối toàn cầu**; S3 CRR cho **nội dung động, theo region cụ thể**.

## 2. CloudFront - ALB/EC2 làm Origin

CloudFront có thể dùng **EC2 instances** hoặc **Application Load Balancers (ALB)** làm origin cho nội dung động.

### A. EC2 Instance làm Origin
*   EC2 instances phải **public** (có public IP).
*   **Security Group** của EC2 phải cho phép traffic từ **IP public của các CloudFront Edge Locations**.
    *   AWS công bố danh sách IP của Edge Locations — bạn phải allow tất cả.
*   Luồng: `Users → Edge Locations → (Public Internet) → EC2 Instance`.

### B. ALB làm Origin
*   ALB phải **public** (internet-facing).
*   EC2 instances phía sau ALB có thể **private** (không cần public IP).
*   **Security Group của ALB** phải allow traffic từ **IP public của CloudFront Edge Locations**.
*   **Security Group của EC2** chỉ cần allow traffic từ **Security Group của ALB**.
*   Luồng: `Users → Edge Locations → (Public Internet) → ALB (public) → EC2 (private)`.

### So sánh

| Khía cạnh | EC2 làm Origin | ALB làm Origin |
|---|---|---|
| **EC2** | Phải **public** | Có thể **private** |
| **Security Group** | Phải allow tất cả IP Edge Location | ALB allow Edge IPs; EC2 chỉ allow ALB SG |
| **Khả năng mở rộng** | Một instance | Cân bằng tải nhiều instances |
| **Khuyến nghị** | Use case đơn giản | Workload production |

### Exam Tips
*   EC2 làm origin → EC2 phải **public**, SG allow IP Edge Locations.
*   ALB làm origin → ALB phải **public**, EC2 phía sau có thể **private**.
*   Dùng ALB **bảo mật hơn** — EC2 không cần public IP.
