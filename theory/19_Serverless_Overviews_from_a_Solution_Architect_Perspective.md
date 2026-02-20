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
