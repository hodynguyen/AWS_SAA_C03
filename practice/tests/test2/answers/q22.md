# Question 22

A company plans to migrate its suite of containerized applications running on-premises to a container service in AWS. The solution must be cloud-agnostic and use an open-source platform that can automatically manage containerized workloads and services.

What should the Solution Architect do to properly migrate and satisfy the given requirement?

## Options

A. Migrate the application to Amazon Container Registry (ECR) with Amazon EC2 instance worker nodes.

B. Migrate the application to Amazon Elastic Kubernetes Service with EKS worker nodes.

C. Migrate the application to Amazon Elastic Container Service with ECS tasks that use the Amazon EC2 launch type.

D. Migrate the application to Amazon Elastic Container Service with ECS tasks that use the AWS Fargate launch type.

## Correct Answer

**B. Migrate the application to Amazon Elastic Kubernetes Service with EKS worker nodes.**

## Explanation

Amazon EKS is a managed Kubernetes service. Kubernetes is an open-source platform that is cloud-agnostic, meaning you can use the same configuration and tools across different cloud providers.

Applications running on Amazon EKS are fully compatible with applications running on any standard Kubernetes environment.

### Why other options are incorrect:

- **A** - ECR is just a container registry, not orchestration.

- **C, D** - ECS is AWS proprietary, not cloud-agnostic.

## References

- https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html
- https://aws.amazon.com/eks/faqs/

## Domain

Design High-Performing Architectures
