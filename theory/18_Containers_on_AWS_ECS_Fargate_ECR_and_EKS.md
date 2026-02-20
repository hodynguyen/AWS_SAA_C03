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

## 3. Amazon ECR (Elastic Container Registry)

Amazon ECR is a **managed Docker container image registry** on AWS.

### Key Features
*   Store, manage, and deploy Docker images.
*   **Private** and **Public** repositories (Public = Amazon ECR Public Gallery).
*   Fully integrated with **ECS** and **EKS**.
*   Access controlled by **IAM** (permissions to push/pull images).
*   Supports **image vulnerability scanning**, **versioning**, **image tags**, **lifecycle policies**.
*   Images are stored in **S3** behind the scenes.

### Exam Tips
*   ECR = **Docker image registry** on AWS.
*   If you see "store Docker images on AWS" → **Amazon ECR**.

## 4. Amazon EKS (Elastic Kubernetes Service)

Amazon EKS is a **managed Kubernetes** service on AWS. Kubernetes is an **open-source** container orchestration system.

### Key Points
*   An alternative to ECS with a **different API** — uses **Kubernetes** (open-source, portable).
*   Supports **EC2 Launch Type** (you manage worker nodes) and **Fargate** (serverless).
*   Use Case: If your company **already uses Kubernetes** on-premises or in another cloud and wants to migrate to AWS.
*   **Cloud-agnostic** — can run on AWS, Azure, GCP, on-premises.

### EKS Node Types
*   **Managed Node Groups**: AWS creates and manages EC2 nodes for you (in an ASG). Supports On-Demand and Spot instances.
*   **Self-Managed Nodes**: You create and register nodes yourself. Supports On-Demand and Spot.
*   **Fargate**: No nodes to manage (serverless).

### Exam Tips
*   EKS = **managed Kubernetes** on AWS.
*   Use EKS if already using Kubernetes or need **cloud-agnostic** container orchestration.
*   Supports same launch types as ECS: **EC2** and **Fargate**.

## 5. AWS App Runner

AWS App Runner is a **fully managed service** to quickly deploy **web applications and APIs** at scale — no infrastructure experience required.

### Key Features
*   Start with **source code** (GitHub) or a **container image** (ECR).
*   Automatically builds, deploys, scales, load balances, encrypts.
*   **VPC access** support for connecting to databases, caches, etc.
*   No Docker/infrastructure knowledge needed.

### Use Cases
*   Web apps, APIs, microservices, rapid production deployments.
*   Perfect for developers who want to **deploy quickly** without managing infrastructure.

### Exam Tips
*   App Runner = **simplest way** to deploy containers/web apps on AWS.
*   If you see "quickly deploy web app from source code or container" with **no infrastructure management** → **App Runner**.

## 6. AWS App2Container

AWS App2Container is a **CLI tool** that helps **migrate existing applications** to containers.

### Key Features
*   Automatically **containerizes** existing **Java** and **.NET** web applications.
*   No code changes needed.
*   Generates **Docker images**, **ECS Task Definitions**, **EKS pod specs**, and **CI/CD pipelines**.

### Exam Tips
*   App2Container = **migrate existing Java/.NET apps** to containers without code changes.
*   CLI tool, generates Docker images + deployment artifacts.

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

## 3. Amazon ECR (Elastic Container Registry)

Amazon ECR là **registry Docker container image được quản lý** trên AWS.

### Tính năng chính
*   Lưu trữ, quản lý, và deploy Docker images.
*   Repository **Private** và **Public** (Public = Amazon ECR Public Gallery).
*   Tích hợp hoàn toàn với **ECS** và **EKS**.
*   Quyền truy cập qua **IAM** (push/pull images).
*   Hỗ trợ **quét lỗ hổng image**, **versioning**, **tags**, **lifecycle policies**.
*   Images được lưu trong **S3** phía sau.

### Exam Tips
*   ECR = **Docker image registry** trên AWS.
*   Thấy "lưu Docker images trên AWS" → **Amazon ECR**.

## 4. Amazon EKS (Elastic Kubernetes Service)

Amazon EKS là dịch vụ **managed Kubernetes** trên AWS. Kubernetes là hệ thống điều phối container **mã nguồn mở**.

### Điểm chính
*   Thay thế ECS với **API khác** — dùng **Kubernetes** (mã nguồn mở, portable).
*   Hỗ trợ **EC2 Launch Type** (bạn quản lý worker nodes) và **Fargate** (serverless).
*   Use Case: Công ty **đã dùng Kubernetes** on-premises hoặc cloud khác và muốn chuyển lên AWS.
*   **Cloud-agnostic** — chạy trên AWS, Azure, GCP, on-premises.

### EKS Node Types
*   **Managed Node Groups**: AWS tạo và quản lý EC2 nodes (trong ASG). Hỗ trợ On-Demand và Spot.
*   **Self-Managed Nodes**: Bạn tự tạo và đăng ký nodes. Hỗ trợ On-Demand và Spot.
*   **Fargate**: Không quản lý nodes (serverless).

### Exam Tips
*   EKS = **managed Kubernetes** trên AWS.
*   Dùng EKS khi đã dùng Kubernetes hoặc cần điều phối **cloud-agnostic**.
*   Hỗ trợ cùng launch types với ECS: **EC2** và **Fargate**.

## 5. AWS App Runner

AWS App Runner là dịch vụ **được quản lý hoàn toàn** để deploy nhanh **web apps và APIs** ở quy mô lớn — không cần kinh nghiệm hạ tầng.

### Tính năng chính
*   Bắt đầu với **source code** (GitHub) hoặc **container image** (ECR).
*   Tự động build, deploy, scale, load balance, mã hóa.
*   Hỗ trợ **VPC access** để kết nối databases, caches, v.v.
*   Không cần kiến thức Docker/hạ tầng.

### Use Cases
*   Web apps, APIs, microservices, deploy nhanh ra production.
*   Phù hợp cho developers muốn **deploy nhanh** không quản lý hạ tầng.

### Exam Tips
*   App Runner = cách **đơn giản nhất** deploy containers/web apps trên AWS.
*   Thấy "deploy nhanh web app từ source code hoặc container" với **không quản lý hạ tầng** → **App Runner**.

## 6. AWS App2Container

AWS App2Container là **công cụ CLI** giúp **migrate ứng dụng hiện tại** sang containers.

### Tính năng chính
*   Tự động **containerize** ứng dụng web **Java** và **.NET** hiện tại.
*   Không cần thay đổi code.
*   Tạo **Docker images**, **ECS Task Definitions**, **EKS pod specs**, và **CI/CD pipelines**.

### Exam Tips
*   App2Container = **migrate ứng dụng Java/.NET** sang containers không cần sửa code.
*   Công cụ CLI, tạo Docker images + deployment artifacts.
