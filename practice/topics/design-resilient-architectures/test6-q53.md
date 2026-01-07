# Question 53

Movie streaming app. Distribute traffic evenly across AZs.

Which feature?

## Options

A. Cross-zone load balancing.

B. Path-based Routing.

C. VPC IP Address Manager (IPAM).

D. Direct Connect SiteLink.

## Correct Answer

**A. Cross-zone load balancing.**

## Explanation

Cross-zone load balancing:
- **Even distribution**: Across all AZs
- **ALB default**: Always enabled
- **NLB optional**: Enable after creation
- **Prevents imbalance**: When AZs have different target counts

### Why other options are incorrect:

- **B** - Path routing routes by URL, not across AZs.

- **C** - IPAM for IP address management.

- **D** - SiteLink for on-premises network connection.

## References

- https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/how-elastic-load-balancing-works.html
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

## Domain

Design Resilient Architectures
