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

## 3. CloudFront - Geo Restriction

Geo Restriction (Geographic Restrictions) allows you to **control which countries** can access your CloudFront distribution.

### How It Works
*   **Allowlist**: Only users from **approved countries** can access your content.
*   **Blocklist**: Users from **specific countries are blocked** from accessing your content.
*   Country is determined using a **3rd-party Geo-IP database** that maps user IP addresses to countries.

### Use Cases
*   **Copyright compliance**: Restrict content distribution to countries where you have distribution rights (e.g., movies, music).
*   **Legal regulations**: Block access from countries under sanctions or legal restrictions.
*   **Content licensing**: Different content availability per region.

### Exam Tips
*   Geo Restriction = **country-level allow/block** on CloudFront.
*   Uses **Geo-IP database** to determine user's country.
*   If you see "restrict content by country" → think **CloudFront Geo Restriction**.

## 4. CloudFront - Cache Invalidation

By default, CloudFront caches content based on TTL. Cache Invalidation lets you **force-remove cached content** from Edge Locations before the TTL expires.

### How It Works
*   When you update content at the origin (e.g., new version of a file), edge caches still serve the **old version** until TTL expires.
*   You can create an **Invalidation** to force CloudFront to remove cached objects.
*   After invalidation, the next request will fetch the **latest version** from the origin.

### Invalidation Paths
*   You specify **path patterns** to invalidate:
    *   `/*` — invalidate **all files** (entire distribution cache).
    *   `/images/*` — invalidate all files under the `/images/` path.
    *   `/index.html` — invalidate a **specific file**.

### Exam Tips
*   Cache Invalidation = **force-refresh cached content** at edge locations.
*   Use when you need users to see **updated content immediately** without waiting for TTL.
*   Invalidating `/*` clears the **entire cache** — use with caution (can increase origin load temporarily).

## 5. AWS Global Accelerator

AWS Global Accelerator improves the **availability and performance** of your applications by routing user traffic through the **AWS Global Network** instead of the public internet.

### The Problem
*   The public internet is unpredictable: traffic goes through many **hops** (routers) with varying latency, packet loss, and congestion.
*   A user in Australia accessing a server in US may experience **high latency** and **variable performance**.

### How It Works
*   Users connect to the **nearest Edge Location** using **2 Anycast static IPs** provided by Global Accelerator.
*   Traffic then travels over the **AWS private global network** (fast, low-latency, redundant) to reach your application.
*   **Anycast IP**: A single IP address that routes to the nearest Edge Location automatically. All Edge Locations announce the same IP.

### Key Features
*   **2 static Anycast IPs** are assigned to your accelerator — these never change.
*   Works with **Elastic IP, EC2 instances, ALB, NLB** — both public and private.
*   **Health Checks**: Automatically detects unhealthy endpoints and performs **instant failover** (< 1 minute).
*   **DDoS Protection**: Integrated with **AWS Shield** for automatic DDoS protection.
*   No client-side caching issues — since IPs are static and don't change.

### CloudFront vs Global Accelerator

| Feature | CloudFront | Global Accelerator |
|---|---|---|
| **Type** | Content Delivery Network (CDN) | Network-level accelerator |
| **Caching** | **Yes** — caches content at edge | **No caching** — proxies traffic |
| **Best for** | **HTTP cacheable content** (images, videos, APIs with caching) | **Non-HTTP** (TCP, UDP), gaming, IoT, VoIP; or HTTP requiring **static IPs** or **fast failover** |
| **IPs** | Uses Edge Location IPs (many, dynamic) | **2 static Anycast IPs** |
| **Protocol** | HTTP/HTTPS only | TCP and UDP |
| **Failover** | Origin failover (configured) | **Automatic, instant** (< 1 min) via health checks |

### Exam Tips
*   Global Accelerator = **AWS private network** + **2 static Anycast IPs** + **instant failover**.
*   Use when you need **static IPs**, **deterministic fast failover**, or **non-HTTP protocols** (TCP/UDP).
*   Use **CloudFront** for cacheable HTTP content; use **Global Accelerator** for everything else.
*   If you see "improve performance for global users" + "static IP" or "TCP/UDP" → think **Global Accelerator**.
*   Both use **Edge Locations** and the **AWS global network**, but for different purposes.

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

## 3. CloudFront - Geo Restriction (Giới hạn địa lý)

Geo Restriction cho phép bạn **kiểm soát quốc gia nào** có thể truy cập CloudFront distribution.

### Cách hoạt động
*   **Allowlist**: Chỉ người dùng từ **các quốc gia được phê duyệt** mới truy cập được.
*   **Blocklist**: Người dùng từ **các quốc gia cụ thể bị chặn** truy cập.
*   Quốc gia được xác định bằng **cơ sở dữ liệu Geo-IP** (bên thứ 3) ánh xạ IP người dùng sang quốc gia.

### Use Cases
*   **Tuân thủ bản quyền**: Giới hạn phân phối nội dung chỉ ở các quốc gia có quyền phân phối (ví dụ: phim, nhạc).
*   **Quy định pháp lý**: Chặn truy cập từ các quốc gia bị cấm vận hoặc hạn chế pháp lý.
*   **Cấp phép nội dung**: Nội dung khả dụng khác nhau theo từng khu vực.

### Exam Tips
*   Geo Restriction = **cho phép/chặn theo quốc gia** trên CloudFront.
*   Dùng **cơ sở dữ liệu Geo-IP** để xác định quốc gia người dùng.
*   Nếu thấy "giới hạn nội dung theo quốc gia" → nghĩ đến **CloudFront Geo Restriction**.

## 4. CloudFront - Cache Invalidation (Xóa cache)

Mặc định, CloudFront cache nội dung theo TTL. Cache Invalidation cho phép bạn **xóa nội dung cache** khỏi Edge Locations trước khi TTL hết hạn.

### Cách hoạt động
*   Khi bạn cập nhật nội dung tại origin (ví dụ: phiên bản mới của file), edge cache vẫn phục vụ **phiên bản cũ** cho đến khi TTL hết hạn.
*   Bạn có thể tạo một **Invalidation** để ép CloudFront xóa các object đã cache.
*   Sau invalidation, request tiếp theo sẽ lấy **phiên bản mới nhất** từ origin.

### Đường dẫn Invalidation
*   Bạn chỉ định **path patterns** để invalidate:
    *   `/*` — invalidate **tất cả file** (toàn bộ cache của distribution).
    *   `/images/*` — invalidate tất cả file trong đường dẫn `/images/`.
    *   `/index.html` — invalidate một **file cụ thể**.

### Exam Tips
*   Cache Invalidation = **ép refresh nội dung cache** tại edge locations.
*   Dùng khi cần người dùng thấy **nội dung mới ngay lập tức** mà không chờ TTL.
*   Invalidate `/*` xóa **toàn bộ cache** — dùng cẩn thận (có thể tăng tải origin tạm thời).

## 5. AWS Global Accelerator

AWS Global Accelerator cải thiện **tính khả dụng và hiệu suất** của ứng dụng bằng cách định tuyến traffic qua **mạng nội bộ toàn cầu của AWS** thay vì internet công cộng.

### Vấn đề
*   Internet công cộng không ổn định: traffic đi qua nhiều **hops** (routers) với độ trễ, mất gói, và tắc nghẽ khác nhau.
*   Người dùng ở Úc truy cập server ở Mỹ có thể gặp **độ trễ cao** và **hiệu suất không ổn định**.

### Cách hoạt động
*   Người dùng kết nối đến **Edge Location gần nhất** sử dụng **2 Anycast static IPs** do Global Accelerator cung cấp.
*   Traffic sau đó đi qua **mạng nội bộ toàn cầu của AWS** (nhanh, độ trễ thấp, dự phòng) để đến ứng dụng.
*   **Anycast IP**: Một địa chỉ IP duy nhất tự động định tuyến đến Edge Location gần nhất. Tất cả Edge Locations cùng quảng bá chung một IP.

### Tính năng chính
*   **2 static Anycast IPs** được gán cho accelerator — không bao giờ thay đổi.
*   Hỗ trợ **Elastic IP, EC2, ALB, NLB** — cả public và private.
*   **Health Checks**: Tự động phát hiện endpoint lỗi và **failover tức thì** (< 1 phút).
*   **Chống DDoS**: Tích hợp với **AWS Shield** tự động bảo vệ.
*   Không vấn đề cache phía client — vì IPs là tĩnh và không thay đổi.

### CloudFront vs Global Accelerator

| Đặc điểm | CloudFront | Global Accelerator |
|---|---|---|
| **Loại** | Content Delivery Network (CDN) | Network-level accelerator |
| **Cache** | **Có** — cache nội dung tại edge | **Không cache** — proxy traffic |
| **Tốt cho** | **HTTP cacheable** (ảnh, video, API có cache) | **Non-HTTP** (TCP, UDP), gaming, IoT, VoIP; hoặc HTTP cần **static IPs** hoặc **failover nhanh** |
| **IPs** | Dùng IP của Edge Locations (nhiều, động) | **2 static Anycast IPs** |
| **Protocol** | Chỉ HTTP/HTTPS | TCP và UDP |
| **Failover** | Origin failover (cấu hình) | **Tự động, tức thì** (< 1 phút) qua health checks |

### Exam Tips
*   Global Accelerator = **mạng nội bộ AWS** + **2 static Anycast IPs** + **failover tức thì**.
*   Dùng khi cần **static IPs**, **failover nhanh và chính xác**, hoặc **giao thức non-HTTP** (TCP/UDP).
*   Dùng **CloudFront** cho HTTP cacheable; dùng **Global Accelerator** cho các trường hợp khác.
*   Nếu thấy "cải thiện hiệu suất cho user toàn cầu" + "static IP" hoặc "TCP/UDP" → nghĩ đến **Global Accelerator**.
*   Cả hai dùng **Edge Locations** và **mạng toàn cầu AWS**, nhưng cho mục đích khác nhau.
