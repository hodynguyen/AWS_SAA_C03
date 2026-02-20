[Vietnamese Below](#vietnamese-version)

# Serverless Overviews from a Solution Architect Perspective

## 1. Serverless Introduction

Serverless is a paradigm where developers **don't manage servers** anymore — they just deploy code/functions.

### What is Serverless?
*   Serverless doesn't mean there are no servers — it means **you don't manage, provision, or see** them.
*   You just deploy code, and the cloud provider handles the rest.

### Serverless Services on AWS
*   **AWS Lambda** — Compute (functions).
*   **Amazon DynamoDB** — NoSQL database.
*   **AWS Cognito** — User authentication.
*   **API Gateway** — Expose APIs.
*   **Amazon S3** — Storage.
*   **Amazon SNS & SQS** — Messaging.
*   **Kinesis Data Firehose** — Streaming data delivery.
*   **Aurora Serverless** — Database.
*   **Step Functions** — Workflow orchestration.
*   **Fargate** — Container compute.

## 2. AWS Lambda

AWS Lambda is a **serverless compute service** — run code without provisioning or managing servers.

### How Lambda Works
*   Upload your code (function), Lambda takes care of everything else.
*   **Event-driven**: Functions are invoked in response to events.
*   **Auto-scaling**: Scales automatically with the number of requests.
*   **Pay per request** + compute time (per 100ms increments).
*   **Free tier**: 1M requests + 400,000 GB-seconds compute/month.

### Benefits
*   **Pricing**: Pay per request and compute time — very cheap.
*   **Languages**: Node.js, Python, Java, C#, Go, Ruby, PowerShell, Custom Runtime (Rust, etc.).
*   **Integrated** with many AWS services.
*   **Up to 10GB RAM** per function.
*   Increasing RAM also improves **CPU and network** performance.

### Common Integrations / Triggers
*   **API Gateway** → Lambda (REST API).
*   **S3** → Lambda (file upload event).
*   **DynamoDB Streams** → Lambda (data change event).
*   **CloudWatch Events / EventBridge** → Lambda (cron, scheduled).
*   **SNS/SQS** → Lambda (message processing).
*   **Kinesis** → Lambda (real-time stream processing).
*   **CloudFront** (Lambda@Edge).
*   **Cognito** (user authentication triggers).

### Lambda Limits (Per Region)

| Limit | Value |
|---|---|
| **Memory** | 128MB – **10GB** (1MB increments) |
| **Timeout** | Max **15 minutes** (900s) |
| **Environment variables** | 4KB |
| **Temp disk space** (`/tmp`) | 512MB – **10GB** |
| **Concurrent executions** | **1000** (can request increase) |
| **Deployment package** | 50MB (zipped), 250MB (unzipped) |
| **Container image** | Max **10GB** |

### Lambda Concurrency
*   **Concurrency** = number of function instances running simultaneously.
*   Default: up to **1000 concurrent** executions per region.
*   If limit reached → **throttling** (synchronous: returns 429, asynchronous: retries then DLQ).

#### Reserved Concurrency
*   Set a **limit** on concurrency for a specific function.
*   Guarantees that function always has that concurrency available.
*   Prevents one function from using all the concurrency.

#### Provisioned Concurrency
*   Pre-initialize a set number of function instances **before invocation**.
*   Eliminates **cold starts** — all invocations have low latency.
*   Managed by **Application Auto Scaling**.

### Lambda SnapStart
*   Improves **Java** function startup performance by up to **10x**.
*   Lambda takes a **snapshot** of the initialized function (memory + disk state).
*   On invocation, restores from snapshot instead of re-initializing.
*   **Only for Java** (Corretto 11+).
*   No additional cost.

### Exam Tips
*   Lambda = **serverless compute**, event-driven, auto-scaling.
*   **Timeout max 15 min** — for longer tasks, use ECS/Fargate/Step Functions.
*   **Memory up to 10GB**, deployment package max 250MB (unzipped).
*   **Concurrency**: 1000 default. Reserved = guarantee. Provisioned = no cold starts.
*   **SnapStart** = faster cold starts for **Java only**.
*   Pay per **request + compute duration**.

## 3. Lambda@Edge & CloudFront Functions

Customize CDN content at the **edge locations** using functions.

### CloudFront Functions
*   **Lightweight** JavaScript functions for **high-scale**, latency-sensitive CDN customizations.
*   **Sub-millisecond** startup, **millions of requests/second**.
*   Used for **Viewer Request/Response** only.
*   Use Cases: Cache key normalization, header manipulation, URL rewrites/redirects, request authentication/authorization.

### Lambda@Edge
*   Full **Lambda functions** in Node.js or Python deployed to edge locations.
*   **Scales to 1000s requests/second**.
*   Used for **Viewer Request/Response** AND **Origin Request/Response**.
*   Use Cases: Longer execution, network access, file system access, request body access.

### CloudFront Functions vs Lambda@Edge

| Feature | CloudFront Functions | Lambda@Edge |
|---|---|---|
| **Language** | JavaScript | Node.js, Python |
| **Scale** | Millions req/s | 1000s req/s |
| **Triggers** | Viewer only | Viewer + Origin |
| **Execution time** | < 1ms | 5–10 seconds |
| **Network/File access** | No | Yes |
| **Pricing** | 1/6 of Lambda@Edge | Higher |

### Exam Tips
*   **CloudFront Functions**: Simple, fast, cheap — viewer-level only.
*   **Lambda@Edge**: Complex logic, origin access, longer execution.

## 4. Lambda in VPC & RDS Integration

### Lambda in VPC
*   By default, Lambda runs **outside your VPC** — can't access private resources (RDS, ElastiCache, etc.).
*   To access VPC resources: define **VPC ID, Subnets, Security Groups**.
*   Lambda creates an **ENI** (Elastic Network Interface) in your subnets.
*   Lambda in VPC can access the **internet** via **NAT Gateway** (in public subnet).
*   Lambda in VPC can access **DynamoDB** via **VPC Endpoint** (Gateway type).

### RDS - Invoking Lambda & Event Notifications
*   **RDS Proxy**: Recommended to use **RDS Proxy** between Lambda and RDS to manage connection pooling (Lambda creates many connections).
*   **RDS Event Notifications**: RDS can send notifications about DB events (creation, failover, etc.) to **SNS** or **EventBridge**.
*   **RDS Invoking Lambda**: RDS (Aurora MySQL/PostgreSQL) can invoke Lambda **from within the database** using stored procedures or triggers.

### Exam Tips
*   Lambda in VPC needs **ENI** + **Security Groups** → can access private resources.
*   Lambda + RDS = use **RDS Proxy** for connection pooling.
*   Lambda + internet from VPC = needs **NAT Gateway**.
*   Lambda + DynamoDB from VPC = use **VPC Endpoint**.

## 5. Amazon DynamoDB

Amazon DynamoDB is a **fully managed, serverless NoSQL database** with single-digit millisecond performance at any scale.

### Key Features
*   **Serverless**: No servers to manage, auto-scaling.
*   **Multi-AZ** replication with high availability.
*   **Scales to massive workloads** — millions of requests/second, trillions of rows, TBs of storage.
*   **Single-digit millisecond** latency on reads and writes.
*   Integrated with **IAM** for security, authorization, and administration.

### Data Model
*   Made of **Tables**, each with a **Primary Key** (decided at creation).
*   Each table has **Items** (rows), and each item has **Attributes** (columns).
*   **Max item size**: **400KB**.
*   Primary Key types:
    *   **Partition Key** only (HASH).
    *   **Partition Key + Sort Key** (HASH + RANGE).

### Capacity Modes

| Mode | Description | Best For |
|---|---|---|
| **Provisioned** | Specify RCU/WCU, can add Auto Scaling | Predictable workloads |
| **On-Demand** | Auto-scales, pay per request | Unpredictable, spiky workloads |

*   **RCU** = Read Capacity Units, **WCU** = Write Capacity Units.

### Advanced Features

#### DynamoDB Accelerator (DAX)
*   **In-memory cache** for DynamoDB — **microsecond** latency.
*   Fully managed, multi-AZ, up to **10x** read performance improvement.
*   No application code changes needed (compatible with DynamoDB APIs).
*   **DAX vs ElastiCache**: DAX is for DynamoDB caching specifically; ElastiCache is general-purpose.

#### DynamoDB Streams
*   **Ordered stream of item-level changes** (create, update, delete) in a table.
*   Stream records can trigger **Lambda functions** for reactions.
*   Use Cases: Real-time reactions, analytics, cross-region replication, derivative tables.
*   Data retained for **24 hours**.

#### DynamoDB Global Tables
*   **Multi-region, multi-active** (read/write in any region) table replication.
*   Must enable **DynamoDB Streams** as prerequisite.
*   **Active-Active**: Apps can read and write in any region.
*   Use Case: Low-latency access for globally distributed users.

#### DynamoDB TTL (Time to Live)
*   Automatically **delete items after an expiration timestamp**.
*   No extra cost, no WCU consumed for deletion.
*   Use Cases: Session data, temporary data, regulatory compliance.

#### DynamoDB - Backups
*   **Continuous backups** using Point-in-Time Recovery (PITR) — last 35 days.
*   **On-demand backups** — long-term retention, until explicitly deleted.
*   Can export to **S3** without affecting read capacity (uses PITR).
*   Can import from **S3** without consuming write capacity.

### Exam Tips
*   DynamoDB = **serverless NoSQL**, single-digit ms latency, 400KB max item.
*   **DAX** = in-memory cache for DynamoDB (microsecond latency).
*   **Streams** = ordered change log → trigger Lambda.
*   **Global Tables** = multi-region, active-active (needs Streams).
*   **TTL** = auto-delete expired items.
*   **On-Demand** = unpredictable; **Provisioned** = predictable workload.

## 6. API Gateway

Amazon API Gateway is a **fully managed service** to create, publish, maintain, and secure **REST, HTTP, and WebSocket APIs**.

### Key Features
*   **Serverless** — no infrastructure to manage.
*   Support for **REST APIs**, **HTTP APIs**, and **WebSocket APIs**.
*   Handles **authentication, throttling, API keys, CORS**.
*   Integrates with **Lambda** (most common), **HTTP endpoints**, **AWS services**.
*   Can **transform** requests and responses.

### Endpoint Types
*   **Edge-Optimized** (default): Requests routed through CloudFront edge locations. API Gateway lives in one region.
*   **Regional**: For clients in the same region. Can manually combine with CloudFront.
*   **Private**: Accessible only from within your **VPC** using VPC Endpoint (ENI).

### Security
*   **IAM Roles**: For AWS users/roles (Sig v4).
*   **Cognito User Pools**: For external users (web/mobile apps).
*   **Lambda Authorizer** (Custom Authorizer): Custom authentication logic via Lambda.
*   **HTTPS**: Custom domain names with ACM (AWS Certificate Manager) certificates.

### Exam Tips
*   API Gateway = **managed API proxy** for Lambda/HTTP/AWS services.
*   **Edge-Optimized** = CloudFront; **Regional** = same region; **Private** = VPC only.
*   Security: **IAM** (internal), **Cognito** (external users), **Lambda Authorizer** (custom logic).
*   If you see "expose Lambda as REST API" → **API Gateway**.

## 7. AWS Step Functions

AWS Step Functions is a **serverless workflow orchestration** service to coordinate multiple AWS services into business workflows.

### Key Features
*   Build workflows as **state machines** using **JSON** (Amazon States Language).
*   Visual workflow designer in the console.
*   Orchestrate **Lambda, ECS, DynamoDB, SQS, SNS, Batch, Glue**, and more.
*   Features: **sequence, parallel, conditions, error handling, retries, timeouts, human approval**.
*   **Max execution time**: **1 year**.

### Use Cases
*   Order processing workflows.
*   Data processing pipelines.
*   Machine learning model training orchestration.
*   Any multi-step business process.

### Exam Tips
*   Step Functions = **visual workflow orchestration** for multiple AWS services.
*   If you see "orchestrate Lambda functions" or "workflow with error handling" → **Step Functions**.
*   Max execution: **1 year** (vs Lambda 15 min).

## 8. Amazon Cognito

Amazon Cognito provides **authentication, authorization, and user management** for web and mobile applications.

### Cognito User Pools (CUP)
*   **Sign-in** functionality for app users.
*   Provides a **serverless user database**.
*   Features: Username/password, MFA, email/phone verification, social login (Google, Facebook, SAML).
*   Returns **JWT tokens** after authentication.
*   Integrates with **API Gateway** and **ALB** for authentication.

### Cognito Identity Pools (Federated Identities)
*   Provide **temporary AWS credentials** to access AWS resources directly.
*   Users can be from Cognito User Pools, 3rd party logins (Google, Facebook), or anonymous.
*   Credentials are mapped to **IAM roles** (with fine-grained policies).
*   Use Case: Allow mobile app user to upload to S3 or access DynamoDB directly.

### CUP vs Identity Pools

| Feature | Cognito User Pools | Cognito Identity Pools |
|---|---|---|
| **Purpose** | Authentication (sign in/up) | Authorization (AWS credentials) |
| **Returns** | JWT tokens | Temporary AWS credentials |
| **Use Case** | User database, login | Access AWS services directly |
| **Integration** | API Gateway, ALB | S3, DynamoDB, any AWS service |

### Exam Tips
*   **User Pools** = sign in/up, user database, JWT tokens → API Gateway/ALB.
*   **Identity Pools** = temporary AWS credentials for direct AWS access.
*   CUP + Identity Pools often used **together**: CUP authenticates → Identity Pool provides AWS credentials.
*   If you see "login for web/mobile app" → **Cognito User Pools**.
*   If you see "give users direct access to S3/DynamoDB" → **Cognito Identity Pools**.

---

<a id="vietnamese-version"></a>

# Serverless Overviews từ góc nhìn Solution Architect

## 1. Giới thiệu Serverless

Serverless là mô hình mà developers **không quản lý servers** nữa — chỉ cần deploy code/functions.

### Serverless là gì?
*   Serverless không có nghĩa là không có servers — mà là **bạn không quản lý, provision, hay nhìn thấy** chúng.
*   Bạn chỉ deploy code, cloud provider lo phần còn lại.

### Các dịch vụ Serverless trên AWS
*   **AWS Lambda** — Compute (functions).
*   **Amazon DynamoDB** — NoSQL database.
*   **AWS Cognito** — Xác thực người dùng.
*   **API Gateway** — Expose APIs.
*   **Amazon S3** — Lưu trữ.
*   **Amazon SNS & SQS** — Messaging.
*   **Kinesis Data Firehose** — Streaming data delivery.
*   **Aurora Serverless** — Database.
*   **Step Functions** — Điều phối workflow.
*   **Fargate** — Container compute.

## 2. AWS Lambda

AWS Lambda là dịch vụ **compute serverless** — chạy code mà không cần provision hay quản lý servers.

### Cách Lambda hoạt động
*   Upload code (function), Lambda lo phần còn lại.
*   **Event-driven**: Functions được gọi khi có sự kiện.
*   **Tự động scale**: Scale theo số lượng requests.
*   **Trả tiền theo request** + thời gian compute (mỗi 100ms).
*   **Free tier**: 1M requests + 400,000 GB-giây compute/tháng.

### Lợi ích
*   **Giá**: Trả per request và compute time — rất rẻ.
*   **Ngôn ngữ**: Node.js, Python, Java, C#, Go, Ruby, PowerShell, Custom Runtime.
*   Tích hợp với nhiều AWS services.
*   Lên tới **10GB RAM** mỗi function.
*   Tăng RAM cũng tăng **CPU và network** performance.

### Các Triggers phổ biến
*   **API Gateway** → Lambda (REST API).
*   **S3** → Lambda (sự kiện upload file).
*   **DynamoDB Streams** → Lambda (sự kiện thay đổi dữ liệu).
*   **CloudWatch Events / EventBridge** → Lambda (cron, scheduled).
*   **SNS/SQS** → Lambda (xử lý messages).
*   **Kinesis** → Lambda (xử lý stream real-time).
*   **CloudFront** (Lambda@Edge).
*   **Cognito** (triggers xác thực người dùng).

### Lambda Limits (Theo Region)

| Limit | Giá trị |
|---|---|
| **Memory** | 128MB – **10GB** (bước 1MB) |
| **Timeout** | Tối đa **15 phút** (900s) |
| **Environment variables** | 4KB |
| **Dung lượng tạm** (`/tmp`) | 512MB – **10GB** |
| **Concurrent executions** | **1000** (có thể xin tăng) |
| **Deployment package** | 50MB (nén), 250MB (giải nén) |
| **Container image** | Tối đa **10GB** |

### Lambda Concurrency
*   **Concurrency** = số function instances chạy đồng thời.
*   Mặc định: tối đa **1000 concurrent** executions mỗi region.
*   Nếu đạt limit → **throttling** (sync: trả 429, async: retry rồi DLQ).

#### Reserved Concurrency
*   Đặt **giới hạn** concurrency cho function cụ thể.
*   Đảm bảo function luôn có sẵn concurrency.
*   Ngăn một function chiếm hết concurrency.

#### Provisioned Concurrency
*   Khởi tạo trước một số function instances **trước khi gọi**.
*   Loại bỏ **cold starts** — tất cả lần gọi đều có độ trễ thấp.
*   Quản lý bởi **Application Auto Scaling**.

### Lambda SnapStart
*   Cải thiện hiệu suất khởi động function **Java** lên tới **10 lần**.
*   Lambda chụp **snapshot** của function đã khởi tạo (memory + disk state).
*   Khi gọi, restore từ snapshot thay vì khởi tạo lại.
*   **Chỉ cho Java** (Corretto 11+).
*   Không tính thêm phí.

### Exam Tips
*   Lambda = **serverless compute**, event-driven, tự động scale.
*   **Timeout tối đa 15 phút** — nhiệm vụ lâu hơn dùng ECS/Fargate/Step Functions.
*   **Memory tối đa 10GB**, deployment package tối đa 250MB (giải nén).
*   **Concurrency**: 1000 mặc định. Reserved = đảm bảo. Provisioned = không cold starts.
*   **SnapStart** = khởi động nhanh cho **Java only**.
*   Trả tiền theo **request + thời gian compute**.

## 3. Lambda@Edge & CloudFront Functions

Tùy chỉnh nội dung CDN tại các **edge locations** bằng functions.

### CloudFront Functions
*   Hàm JavaScript **nhẹ** cho tùy chỉnh CDN **quy mô lớn**, độ trễ thấp.
*   Khởi động **dưới mili giây**, **hàng triệu requests/giây**.
*   Chỉ dùng cho **Viewer Request/Response**.
*   Use Cases: Chuẩn hóa cache key, thao tác header, rewrite/redirect URL, xác thực request.

### Lambda@Edge
*   Hàm **Lambda đầy đủ** (Node.js hoặc Python) deploy đến edge locations.
*   Scale lên **hàng nghìn requests/giây**.
*   Dùng cho **Viewer Request/Response** VÀ **Origin Request/Response**.
*   Use Cases: Logic phức tạp, truy cập mạng, file system, request body.

### CloudFront Functions vs Lambda@Edge

| Đặc điểm | CloudFront Functions | Lambda@Edge |
|---|---|---|
| **Ngôn ngữ** | JavaScript | Node.js, Python |
| **Scale** | Hàng triệu req/s | Hàng nghìn req/s |
| **Triggers** | Chỉ Viewer | Viewer + Origin |
| **Thời gian** | < 1ms | 5–10 giây |
| **Mạng/File** | Không | Có |
| **Giá** | 1/6 Lambda@Edge | Cao hơn |

### Exam Tips
*   **CloudFront Functions**: Đơn giản, nhanh, rẻ — chỉ viewer-level.
*   **Lambda@Edge**: Logic phức tạp, truy cập origin, chạy lâu hơn.

## 4. Lambda trong VPC & Tích hợp RDS

### Lambda trong VPC
*   Mặc định, Lambda chạy **ngoài VPC** — không truy cập được tài nguyên private (RDS, ElastiCache, v.v.).
*   Để truy cập VPC: định nghĩa **VPC ID, Subnets, Security Groups**.
*   Lambda tạo **ENI** (Elastic Network Interface) trong subnets của bạn.
*   Lambda trong VPC muốn truy cập **internet** qua **NAT Gateway** (trong public subnet).
*   Lambda trong VPC truy cập **DynamoDB** qua **VPC Endpoint** (Gateway type).

### RDS - Gọi Lambda & Event Notifications
*   **RDS Proxy**: Nên dùng **RDS Proxy** giữa Lambda và RDS để quản lý connection pooling.
*   **RDS Event Notifications**: RDS gửi thông báo về DB events (tạo, failover, v.v.) đến **SNS** hoặc **EventBridge**.
*   **RDS Gọi Lambda**: RDS (Aurora MySQL/PostgreSQL) có thể gọi Lambda **từ bên trong database** qua stored procedures hoặc triggers.

### Exam Tips
*   Lambda trong VPC cần **ENI** + **Security Groups** → truy cập tài nguyên private.
*   Lambda + RDS = dùng **RDS Proxy** cho connection pooling.
*   Lambda + internet từ VPC = cần **NAT Gateway**.
*   Lambda + DynamoDB từ VPC = dùng **VPC Endpoint**.

## 5. Amazon DynamoDB

Amazon DynamoDB là **cơ sở dữ liệu NoSQL serverless, được quản lý hoàn toàn** với hiệu suất mili giây đơn ở mọi quy mô.

### Tính năng chính
*   **Serverless**: Không quản lý servers, tự động scale.
*   Replicate **Multi-AZ** với tính sẵn sàng cao.
*   **Scale đến workloads khổng lồ** — hàng triệu requests/giây, hàng tỷ rows, TBs storage.
*   Độ trễ **mili giây đơn** khi đọc và ghi.
*   Tích hợp **IAM** cho bảo mật và quản trị.

### Mô hình dữ liệu
*   Gồm **Tables**, mỗi bảng có **Primary Key** (quyết định khi tạo).
*   Mỗi bảng có **Items** (hàng), mỗi item có **Attributes** (cột).
*   **Kích thước item tối đa**: **400KB**.
*   Loại Primary Key:
    *   **Partition Key** (HASH).
    *   **Partition Key + Sort Key** (HASH + RANGE).

### Capacity Modes

| Mode | Mô tả | Phù hợp cho |
|---|---|---|
| **Provisioned** | Chỉ định RCU/WCU, có thể Auto Scaling | Workloads có thể dự đoán |
| **On-Demand** | Tự động scale, trả per request | Workloads không dự đoán, spiky |

*   **RCU** = Read Capacity Units, **WCU** = Write Capacity Units.

### Tính năng nâng cao

#### DynamoDB Accelerator (DAX)
*   **Cache trong bộ nhớ** cho DynamoDB — độ trễ **micro giây**.
*   Fully managed, multi-AZ, cải thiện hiệu suất đọc lên tới **10 lần**.
*   Không cần thay đổi code (tương thích DynamoDB APIs).
*   **DAX vs ElastiCache**: DAX chuyên cho DynamoDB; ElastiCache là đa dụng.

#### DynamoDB Streams
*   **Luồng thay đổi có thứ tự** (tạo, sửa, xóa) trong bảng.
*   Có thể trigger **Lambda functions** để phản ứng.
*   Use Cases: Phản ứng real-time, analytics, replicate cross-region.
*   Dữ liệu lưu **24 giờ**.

#### DynamoDB Global Tables
*   Replicate bảng **đa region, đa active** (đọc/ghi bất kỳ region nào).
*   Cần bật **DynamoDB Streams** trước.
*   **Active-Active**: Ứng dụng có thể đọc và ghi ở mọi region.
*   Use Case: Truy cập độ trễ thấp cho người dùng toàn cầu.

#### DynamoDB TTL (Time to Live)
*   Tự động **xóa items sau mốc thời gian hết hạn**.
*   Không tốn thêm phí, không tính WCU.
*   Use Cases: Session data, dữ liệu tạm, tuân thủ quy định.

#### DynamoDB - Backups
*   **Continuous backups** với Point-in-Time Recovery (PITR) — 35 ngày gần nhất.
*   **On-demand backups** — lưu dài hạn, cho đến khi xóa thủ công.
*   Export sang **S3** không ảnh hưởng read capacity (dùng PITR).
*   Import từ **S3** không tốn write capacity.

### Exam Tips
*   DynamoDB = **serverless NoSQL**, độ trễ ms đơn, item tối đa 400KB.
*   **DAX** = cache trong bộ nhớ cho DynamoDB (độ trễ micro giây).
*   **Streams** = log thay đổi có thứ tự → trigger Lambda.
*   **Global Tables** = đa region, active-active (cần Streams).
*   **TTL** = tự động xóa items hết hạn.
*   **On-Demand** = không dự đoán; **Provisioned** = workload ổn định.

## 6. API Gateway

Amazon API Gateway là dịch vụ **được quản lý hoàn toàn** để tạo, publish, duy trì và bảo mật **REST, HTTP, và WebSocket APIs**.

### Tính năng chính
*   **Serverless** — không quản lý hạ tầng.
*   Hỗ trợ **REST APIs**, **HTTP APIs**, và **WebSocket APIs**.
*   Xử lý **authentication, throttling, API keys, CORS**.
*   Tích hợp với **Lambda** (phổ biến nhất), **HTTP endpoints**, **AWS services**.
*   Có thể **biến đổi** requests và responses.

### Endpoint Types
*   **Edge-Optimized** (mặc định): Requests qua CloudFront edge locations.
*   **Regional**: Cho clients cùng region. Có thể kết hợp CloudFront thủ công.
*   **Private**: Chỉ truy cập từ **VPC** qua VPC Endpoint (ENI).

### Bảo mật
*   **IAM Roles**: Cho AWS users/roles (Sig v4).
*   **Cognito User Pools**: Cho người dùng bên ngoài (web/mobile apps).
*   **Lambda Authorizer**: Logic xác thực tùy chỉnh qua Lambda.
*   **HTTPS**: Custom domain với ACM (AWS Certificate Manager) certificates.

### Exam Tips
*   API Gateway = **managed API proxy** cho Lambda/HTTP/AWS services.
*   **Edge-Optimized** = CloudFront; **Regional** = cùng region; **Private** = chỉ VPC.
*   Bảo mật: **IAM** (nội bộ), **Cognito** (người dùng ngoài), **Lambda Authorizer** (tùy chỉnh).
*   Thấy "expose Lambda as REST API" → **API Gateway**.

## 7. AWS Step Functions

AWS Step Functions là dịch vụ **điều phối workflow serverless** để phối hợp nhiều AWS services thành business workflows.

### Tính năng chính
*   Xây dựng workflows là **state machines** bằng **JSON** (Amazon States Language).
*   Công cụ thiết kế workflow trực quan trong console.
*   Điều phối **Lambda, ECS, DynamoDB, SQS, SNS, Batch, Glue**, và nhiều hơn.
*   Tính năng: **sequence, parallel, conditions, xử lý lỗi, retry, timeout, phê duyệt thủ công**.
*   **Thời gian thực thi tối đa**: **1 năm**.

### Use Cases
*   Quy trình xử lý đơn hàng.
*   Pipeline xử lý dữ liệu.
*   Điều phối training mô hình ML.
*   Mọi quy trình business nhiều bước.

### Exam Tips
*   Step Functions = **điều phối workflow trực quan** cho nhiều AWS services.
*   Thấy "orchestrate Lambda" hoặc "workflow với xử lý lỗi" → **Step Functions**.
*   Thời gian thực thi tối đa: **1 năm** (vs Lambda 15 phút).

## 8. Amazon Cognito

Amazon Cognito cung cấp **xác thực, ủy quyền, và quản lý người dùng** cho ứng dụng web và mobile.

### Cognito User Pools (CUP)
*   Chức năng **đăng nhập** cho người dùng ứng dụng.
*   Cung cấp **user database serverless**.
*   Tính năng: Username/password, MFA, xác minh email/phone, social login (Google, Facebook, SAML).
*   Trả về **JWT tokens** sau xác thực.
*   Tích hợp với **API Gateway** và **ALB** cho xác thực.

### Cognito Identity Pools (Federated Identities)
*   Cung cấp **temporary AWS credentials** để truy cập AWS resources trực tiếp.
*   Người dùng từ Cognito User Pools, 3rd party logins, hoặc anonymous.
*   Credentials được map vào **IAM roles**.
*   Use Case: Cho phép người dùng mobile upload S3 hoặc truy cập DynamoDB trực tiếp.

### CUP vs Identity Pools

| Đặc điểm | Cognito User Pools | Cognito Identity Pools |
|---|---|---|
| **Mục đích** | Xác thực (đăng nhập/ký) | Ủy quyền (AWS credentials) |
| **Trả về** | JWT tokens | Temporary AWS credentials |
| **Use Case** | User database, login | Truy cập AWS services trực tiếp |
| **Tích hợp** | API Gateway, ALB | S3, DynamoDB, mọi AWS service |

### Exam Tips
*   **User Pools** = đăng nhập/ký, user database, JWT tokens → API Gateway/ALB.
*   **Identity Pools** = temporary AWS credentials cho truy cập AWS trực tiếp.
*   CUP + Identity Pools thường dùng **cùng nhau**: CUP xác thực → Identity Pool cấp AWS credentials.
*   Thấy "login cho web/mobile app" → **Cognito User Pools**.
*   Thấy "cho người dùng truy cập trực tiếp S3/DynamoDB" → **Cognito Identity Pools**.
