# Question 60

An application requires a minimum of 4 EC2 instances running at all times for fault tolerance.

Which deployment is the best option?

## Options

A. 2 instances in each of 2 Availability Zones behind ALB.

B. 4 instances in one Availability Zone behind ALB.

C. 1 instance in each of 4 Availability Zones behind ALB.

D. 2 instances in each of 3 Availability Zones behind ALB.

## Correct Answer

**D. 2 instances in each of 3 Availability Zones behind ALB.**

## Explanation

Fault tolerance = maintain minimum instances even if one AZ fails:
- **2+2+2 in 3 AZs**: If one AZ fails → 4 instances remain ✓
- Total 6 instances ensures 4 survive any single AZ failure

### Why other options are incorrect:

- **A** - 2+2 in 2 AZs: If one fails → only 2 instances remain.

- **B** - All in one AZ: If it fails → 0 instances remain.

- **C** - 1 per AZ: If one fails → only 3 instances remain.

## References

- https://media.amazonwebservices.com/AWS_Building_Fault_Tolerant_Applications.pdf
- https://tutorialsdojo.com/amazon-ec2/

## Domain

Design Resilient Architectures
