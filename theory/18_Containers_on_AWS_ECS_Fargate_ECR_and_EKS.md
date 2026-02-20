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
