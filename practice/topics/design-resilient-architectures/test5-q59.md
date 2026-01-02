# Question 59

EKS e-commerce app has holiday traffic surges. Need auto-scaling with LEAST operational overhead. (Select TWO.)

## Options

A. Metrics Server + Horizontal Pod Autoscaler.

B. Metrics Server + Vertical Pod Autoscaler.

C. CloudWatch Alarms for scaling.

D. Cluster Autoscaler.

E. Karpenter for node scaling.

## Correct Answer

**A. Metrics Server + Horizontal Pod Autoscaler.**

**E. Karpenter for node scaling.**

## Explanation

Two-level scaling:
1. **Horizontal Pod Autoscaler**: Scales pods based on metrics
2. **Karpenter**: Auto-provisions nodes with optimal instance types

Karpenter is faster and more flexible than Cluster Autoscaler.

### Why other options are incorrect:

- **B** - Vertical scaling (up/down) is different from horizontal (in/out).

- **C** - CloudWatch alarms add latency to scaling response.

- **D** - Cluster Autoscaler works but slower than Karpenter, more config needed.

## References

- https://docs.aws.amazon.com/eks/latest/userguide/horizontal-pod-autoscaler.html
- https://tutorialsdojo.com/amazon-elastic-kubernetes-service-eks/

## Domain

Design Resilient Architectures
