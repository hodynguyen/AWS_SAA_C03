[Vietnamese Below](#vietnamese-version)

# Route 53 - Cheat Sheet

*   **Domain Registrar**
*   **Functions**: Domain registration, DNS Routing, Health Checking.
*   **Hosted Zone**: Container for all DNS Records for a specific Domain.
    *   **Private Hosted Zone**: Only accessible within VPC.
    *   **Public Hosted Zone**: Accessible from the Internet.

## 1. DNS Records

*   **A**: Maps domain -> IPv4.
*   **AAAA**: Maps domain -> IPv6.
*   **CNAME**: Maps hostname to another hostname (subdomain).
*   **NS**: Name Servers (specifies which DNS server cluster manages this domain. *Example*: if domain is bought on GoDaddy but you want Route53 to manage it, you need to point Route53's name servers to this record on GoDaddy).

## 2. Alias Records

*   Points hostname -> **AWS Resource**.
*   **Features**:
    *   Can replace CNAME, used for pointing root domain (Zone Apex).
    *   **Faster** than CNAME as AWS optimizes it (Route53 returns IP directly instead of returning domain like CNAME).
    *   **Cheaper** than CNAME if pointing to AWS Resource (free).
    *   **Use CNAME** when destination is **not** an AWS resource.

## 3. Routing Policy

*   **Concept**: Similar to ELB in directing traffic, but Route53 operates at **DNS Layer** (works with IP), while ELB operates at **Network/App Layer** (works with data).
*   **Scope**: Route53 directs traffic globally (Macro - Region, DC), while LB directs traffic locally (Micro - server, specific request).
*   **7 Types of Routing Policies**:
    1.  **Simple**: Default. Round robin to IPs attached to domain. **No health check support** -> Small sites or Dev/Test.
    2.  **Weighted**: Assigns a weight to each record (e.g., 80/20 or 50/30/20). Percentage of traffic to resources -> Used for **A/B Testing** (test on 10% users), **Blue/Green Deployment** (gradually shift users to new version to reduce risk), or **Manual LB** (Server A is twice as strong as Server B -> set weight 2:1).
    3.  **Latency-Based**: AWS maps speed from user to Regions -> returns IP of server in Region with **lowest latency** -> Used for **Global Apps, Performance**.
    4.  **Failover**: Has **Primary** and **Secondary** records. Traffic normally goes to Primary, if Primary fails, it goes to Secondary -> Used for **Disaster Recovery (DR)** or maintenance sites.
    5.  **Geolocation**: Checks user IP origin -> returns IP of server in that location (Different from Latency: Latency cares about speed, Geo cares about location) -> Used for **compliance/language-specific content**, data sovereignty.
    6.  **Geoproximity**: Similar to Geolocation but adds **Bias** concept to expand or shrink a server's coverage area -> Used for extremely granular traffic coordination, mandatory to use **Traffic Flow (Visual Editor)**.
    7.  **Multivalue**: Like Simple but with **Health Checks** -> Used as alternative to ELB, provides LB and HA but **cheaper**.

## 4. Health Check

*   **Endpoint HC**: Pings IP/domain -> Used for public, standard sites.
*   **Calculated HC**: Aggregates multiple health checks (e.g., healthy only if 3/5 servers are up).
*   **CloudWatch Alarm HC**: Used for private resources.
*   **Configuration**: **Interval** (30s or 10s) and **Threshold** (Number of consecutive failures to conclude unhealthy).
*   **Security Group**: Must **allow** AWS Health Checkers IP range, otherwise it will always be unhealthy.

---

<a id="vietnamese-version"></a>

# Route 53

*   Là **Domain Registrar**.
*   Có các chức năng như: Đăng kí tên miền, DNS Routing, Health Checking.
*   **Hosted Zone**: Là container chứa tất cả DNS Record cho một Domain cụ thể.
    *   **Private Hosted Zone**: Chỉ truy cập được trong VPC.
    *   **Public Hosted Zone**: Cho phép truy cập từ Internet.

## 1. DNS Records

*   **A**: Map domain -> IPv4.
*   **AAAA**: Map domain -> IPv6.
*   **CNAME**: Sub domain.
*   **NS**: Name servers (chỉ định cụm máy chủ DNS nào nào quản lý domain này, ví dụ mua domain ở Godaddy nhưng muốn Route53 quản lý thì cần point name servers của Route53 vào bản ghi này trên GoDaddy).

## 2. Alias Records

*   Point hostname -> **AWS resource**.
*   **Đặc điểm**:
    *   Có thể thay thế CNAME, trong case cần point root domain.
    *   **Nhanh hơn** CNAME do được AWS tối ưu (Route53 trả thẳng về IP thay vì trả về domain nếu dùng CNAME).
    *   **Rẻ hơn** CNAME nếu trỏ vào AWS Resource (fee = 0).
    *   Dùng CNAME khi des **không phải** AWS resource.

## 3. Routing Policy

*   **Khái niệm**: Giống ELB ở phần đều là điều hướng traffic, nhưng Route53 hoạt động ở tầng **DNS** (làm việc với IP), còn ELB hoạt động ở tầng **network/app** (làm việc với data).
*   **Phạm vi**: Route53 điều hướng vĩ mô (Region, DC) còn LB điều hướng vi mô (server, request cụ thể).
*   **7 loại routing policy**:
    1.  **Simple**: Loại mặc định, round robin đến các ip được gắn vào domain, **không hỗ trợ health check** -> site nhỏ hoặc dev/test.
    2.  **Weighted**: Gán cho mỗi record một trọng số, ví dụ 80/20 hoặc 50/30/20, … là tỉ lệ % đến các resource khác nhau -> dùng cho **A/B testing** (test trên 10% lượng user). **Blue/green deployment** (chuyển từ tử user sang bản mới để giảm rủi ro), hoặc dùng làm **LB thủ công** (server A mạnh gấp đôi server B thì set weight 2:1).
    3.  **Latency-Based**: AWS có bản đồ tốc độ từ user đến các Region -> trả về cho user IP của server nằm ở Region có **độ trễ thấp nhất** -> dùng cho **Global App, Performance**.
    4.  **Failover**: Có hai records **Primary** và **Secondary**, traffic bình thường đổ vào P, khi nào P fail đổ vào S -> dùng S cho site bảo trì hoặc trang dự phòng.
    5.  **Geolocation**: Check IP xem user đến từ đâu -> trả về IP server ở đó (khác Latency, Latency quan tâm tốc độ, Geo quan tâm vị trí) -> dùng khi liên quan đến **compliance/language-specific**, tuân thủ dữ liệu.
    6.  **Geoproximity**: Giống Geolocation nhưng thêm khái niệm **Bias**, mở rộng hoặc thu hẹp vùng phủ sóng của một server -> dùng khi điều phối traffic cực kì chi tiết, bắt buộc phải dùng **Traffic Flow (Visual Editor)**.
    7.  **Multivalue**: Giống simple nhưng có **health check** -> dùng thay ELB, có LB và HA nhưng **giá rẻ hơn**.

## 4. Health Check

*   **Endpoint HC**: Ping vào IP/domain, dùng cho public, site thông thường.
*   **Calculated HC**: Gộp nhiều health check lại, ví dụ chỉ healthy nếu 3/5 server sống.
*   **CloudWatch Alarm HC**: Dùng cho server private.
*   **Cấu hình**: **Interval** (30s hoặc 10s) và **Threshold** (Số lần fail liên tiếp để kết luận).
*   **Security Group**: Phải **open** cho dải IP của AWS Health Checkers, nếu k sẽ luôn unhealthy.
