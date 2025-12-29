# Question 26

A company uses Amazon EKS for container applications. Workload varies throughout the day, and infrastructure needs to auto-scale with minimal overhead.

Which solution meets the requirements?

## Options

A. Integrate edge-optimized API Gateway endpoint with EKS to manage APIs.

B. Set up CloudWatch alarms for CPU/request count to monitor EKS metrics.

C. Use EC2 Auto Scaling Groups with custom policies to manage EKS worker nodes.

D. Use Kubernetes Metrics and Kubernetes Cluster Autoscaler to manage nodes.

## Correct Answer

**D. Use Kubernetes Metrics and Kubernetes Cluster Autoscaler to manage nodes.**

## Explanation

EKS supports two autoscaling mechanisms:
- **Horizontal Pod Autoscaler (HPA)**: Scales pods based on CPU/memory metrics
- **Cluster Autoscaler**: Adjusts node count based on pending pods

Together, they provide seamless Kubernetes-native scaling with minimal configuration—no custom policies or Lambda functions needed.

### Why other options are incorrect:

- **A** - API Gateway manages API exposure, not scaling.

- **B** - CloudWatch alarms monitor but don't trigger EKS scaling directly.

- **C** - EC2 Auto Scaling Groups require more configuration than Cluster Autoscaler.

## References

- https://docs.aws.amazon.com/eks/latest/userguide/autoscaling.html
- https://tutorialsdojo.com/amazon-elastic-kubernetes-service-eks/

## Domain

Design Resilient Architectures
