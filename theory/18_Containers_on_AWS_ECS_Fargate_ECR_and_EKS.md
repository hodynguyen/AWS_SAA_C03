[Vietnamese Below](#vietnamese-version)

# Containers on AWS: ECS, Fargate, ECR & EKS

## 1. Docker Introduction

Docker is a **container technology** that packages applications with all their dependencies into **standardized units** (containers) for software development.

### What is Docker?
*   Apps are packaged in **containers** that can run on **any OS** consistently.
*   Containers share the host OS kernel — **lighter and faster** than VMs.
*   Images are stored in **Docker repositories**:
    *   **Docker Hub** — public repository.
    *   **Amazon ECR** (Elastic Container Registry) — AWS private/public repository.

### Docker vs Virtual Machines
*   **VMs**: Each VM has its own **full OS** → heavy, slow to start, uses more resources.
*   **Containers**: Share the host kernel, only package the **app + dependencies** → lightweight, fast start, efficient.

### Docker on AWS
*   **Amazon ECS** (Elastic Container Service) — AWS container orchestration.
*   **Amazon EKS** (Elastic Kubernetes Service) — Managed Kubernetes.
*   **AWS Fargate** — Serverless container compute (no servers to manage).
*   **Amazon ECR** — Store Docker images.

## 2. Amazon ECS (Elastic Container Service)

Amazon ECS is AWS's **container orchestration service** to run and manage Docker containers.

### Launch Types

#### A. EC2 Launch Type
*   **You manage** the EC2 instances (infrastructure).
*   Each EC2 instance runs an **ECS Agent** that registers it with the ECS cluster.
*   AWS takes care of starting/stopping containers.
*   You're responsible for provisioning, patching, scaling EC2 instances.

#### B. Fargate Launch Type
*   **Serverless** — no EC2 instances to manage.
*   You only define **Task Definitions** (CPU, memory, Docker image).
*   AWS runs the containers for you — just works.
*   To scale: just increase the **number of tasks**.

### IAM Roles for ECS
*   **EC2 Instance Profile** (EC2 Launch Type only):
    *   Used by the **ECS Agent** to make API calls to ECS, pull images from ECR, send logs to CloudWatch.
*   **ECS Task Role**:
    *   Each **task** can have its own IAM role — defined in the **Task Definition**.
    *   Allows different tasks to access different AWS services.
    *   Example: Task A accesses S3, Task B accesses DynamoDB.

### Load Balancer Integration
*   **ALB**: Supported and **recommended** for most use cases.
*   **NLB**: For high throughput/performance, or to pair with **AWS Private Link**.
*   **CLB**: Supported but **not recommended** (no advanced features).

### Data Persistence - EFS
*   Mount **Amazon EFS** file system onto ECS tasks.
*   Works for both **EC2** and **Fargate** launch types.
*   Tasks in any AZ can share the same data.
*   **Fargate + EFS** = fully **serverless** data persistence.
*   **Note**: S3 cannot be mounted as a file system on ECS tasks.

### ECS Auto Scaling
*   Auto scale the **number of ECS tasks** based on:
    *   **CPU Utilization**.
    *   **Memory Utilization**.
    *   **ALB Request Count Per Target**.
*   Uses **AWS Application Auto Scaling**.
*   Scaling strategies:
    *   **Target Tracking**: Scale based on a target metric value.
    *   **Step Scaling**: Scale based on CloudWatch Alarms.
    *   **Scheduled Scaling**: Scale based on predictable patterns.
*   **EC2 Launch Type**: Also need to scale the EC2 instances (use **ASG** or **ECS Cluster Capacity Provider**).
*   **Fargate**: Auto Scaling is much easier — just scale tasks.

### ECS Solutions Architectures
*   **ECS + EventBridge**: S3 event → EventBridge → run ECS task (e.g., process uploaded file).
*   **ECS + EventBridge Schedule**: Schedule ECS tasks to run periodically (cron jobs).
*   **ECS + SQS**: ECS tasks poll SQS queue, auto scale tasks based on queue length.

### Exam Tips
*   **EC2 Launch Type**: You manage EC2, ECS Agent runs on instances.
*   **Fargate**: Serverless, no EC2 to manage, scale by task count.
*   **Task Role** = per-task IAM permissions; **Instance Profile** = ECS Agent permissions.
*   **EFS** works with both EC2 and Fargate; S3 cannot be mounted.
*   Scale tasks with **Application Auto Scaling**; scale EC2 with **Capacity Provider/ASG**.

---

<a id="vietnamese-version"></a>

# Containers on AWS: ECS, Fargate, ECR & EKS

## 1. Giới thiệu Docker

Docker là **công nghệ container** đóng gói ứng dụng cùng tất cả dependencies thành **đơn vị chuẩn hóa** (containers) cho phát triển phần mềm.

### Docker là gì?
*   Ứng dụng được đóng gói trong **containers** có thể chạy trên **mọi OS** đồng nhất.
*   Containers chia sẻ kernel của host OS — **nhẹ hơn và nhanh hơn** VMs.
*   Images được lưu trong **Docker repositories**:
    *   **Docker Hub** — repository công khai.
    *   **Amazon ECR** (Elastic Container Registry) — repository riêng/công khai của AWS.

### Docker vs Virtual Machines
*   **VMs**: Mỗi VM có **OS đầy đủ** riêng → nặng, khởi động chậm, tốn tài nguyên.
*   **Containers**: Chia sẻ kernel host, chỉ đóng gói **app + dependencies** → nhẹ, khởi động nhanh, hiệu quả.

### Docker trên AWS
*   **Amazon ECS** — Điều phối container của AWS.
*   **Amazon EKS** — Managed Kubernetes.
*   **AWS Fargate** — Compute container serverless (không quản lý server).
*   **Amazon ECR** — Lưu trữ Docker images.

## 2. Amazon ECS (Elastic Container Service)

Amazon ECS là dịch vụ **điều phối container** của AWS để chạy và quản lý Docker containers.

### Launch Types

#### A. EC2 Launch Type
*   **Bạn quản lý** các EC2 instances (hạ tầng).
*   Mỗi EC2 chạy **ECS Agent** đăng ký vào ECS cluster.
*   AWS lo việc start/stop containers.
*   Bạn chịu trách nhiệm provision, vá lỗi, scale EC2.

#### B. Fargate Launch Type
*   **Serverless** — không cần quản lý EC2.
*   Chỉ cần định nghĩa **Task Definitions** (CPU, memory, Docker image).
*   AWS chạy containers cho bạn.
*   Scale: chỉ cần tăng **số lượng tasks**.

### IAM Roles cho ECS
*   **EC2 Instance Profile** (chỉ EC2 Launch Type):
    *   Dùng bởi **ECS Agent** để gọi API ECS, pull images từ ECR, gửi logs vào CloudWatch.
*   **ECS Task Role**:
    *   Mỗi **task** có thể có IAM role riêng — định nghĩa trong **Task Definition**.
    *   Cho phép các tasks truy cập AWS services khác nhau.
    *   Ví dụ: Task A truy cập S3, Task B truy cập DynamoDB.

### Tích hợp Load Balancer
*   **ALB**: Được hỗ trợ và **khuyến nghị** cho hầu hết use cases.
*   **NLB**: Cho throughput/hiệu suất cao, hoặc dùng với **AWS Private Link**.
*   **CLB**: Hỗ trợ nhưng **không khuyến nghị**.

### Lưu trữ dữ liệu - EFS
*   Mount **Amazon EFS** lên ECS tasks.
*   Hoạt động với cả **EC2** và **Fargate** launch types.
*   Tasks ở bất kỳ AZ nào đều chia sẻ cùng dữ liệu.
*   **Fargate + EFS** = lưu trữ **serverless** hoàn toàn.
*   **Lưu ý**: S3 không thể mount làm file system cho ECS tasks.

### ECS Auto Scaling
*   Tự động scale **số lượng ECS tasks** dựa trên:
    *   **CPU Utilization**.
    *   **Memory Utilization**.
    *   **ALB Request Count Per Target**.
*   Dùng **AWS Application Auto Scaling**.
*   Chiến lược scale:
    *   **Target Tracking**: Scale theo giá trị metric mục tiêu.
    *   **Step Scaling**: Scale theo CloudWatch Alarms.
    *   **Scheduled Scaling**: Scale theo lịch định.
*   **EC2 Launch Type**: Cần scale cả EC2 (dùng **ASG** hoặc **ECS Cluster Capacity Provider**).
*   **Fargate**: Auto Scaling dễ hơn — chỉ scale tasks.

### ECS Solutions Architectures
*   **ECS + EventBridge**: S3 event → EventBridge → chạy ECS task (ví dụ: xử lý file upload).
*   **ECS + EventBridge Schedule**: Lên lịch ECS tasks chạy định kỳ (cron jobs).
*   **ECS + SQS**: ECS tasks poll SQS queue, scale tasks theo độ dài queue.

### Exam Tips
*   **EC2 Launch Type**: Bạn quản lý EC2, ECS Agent chạy trên instances.
*   **Fargate**: Serverless, không quản lý EC2, scale theo số tasks.
*   **Task Role** = quyền IAM từng task; **Instance Profile** = quyền ECS Agent.
*   **EFS** hoạt động với cả EC2 và Fargate; S3 không thể mount.
*   Scale tasks bằng **Application Auto Scaling**; scale EC2 bằng **Capacity Provider/ASG**.
