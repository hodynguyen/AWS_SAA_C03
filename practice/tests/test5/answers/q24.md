# Question 24

A company migrates an on-premises app to AWS with zero downtime. They want to divert 50% traffic to AWS, 50% to on-premises. VPC connects to on-premises via Direct Connect.

Which solutions work? (Select TWO.)

## Options

A. Route 53 with Weighted routing policy.

B. Route 53 with Failover routing policy.

C. ALB with Weighted Target Groups.

D. NLB with Weighted Target Groups.

E. AWS Global Accelerator with Direct Connect Gateway.

## Correct Answer

**A. Route 53 with Weighted routing policy.**

**C. ALB with Weighted Target Groups.**

## Explanation

Two valid approaches:
- **Route 53 Weighted**: DNS-level traffic splitting by weight
- **ALB Weighted Target Groups**: Load balancer splits traffic by weight to IP targets (on-premises via Direct Connect)

### Why other options are incorrect:

- **B** - Failover is active/passive, not weighted distribution.

- **D** - NLB doesn't support weighted target groups.

- **E** - Global Accelerator works, but AnyCast IP for on-premises isn't correct.

## References

- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html
- https://tutorialsdojo.com/amazon-route-53/

## Domain

Design High-Performing Architectures
