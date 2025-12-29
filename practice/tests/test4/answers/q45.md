# Question 45

An e-commerce application requires 6 EC2 instances running at all times. The region has 3 AZs.

Which deployments provide 100% fault tolerance if any single AZ fails? (Select TWO.)

## Options

A. 3 instances in AZ-a, 3 in AZ-b, 3 in AZ-c

B. 2 instances in AZ-a, 2 in AZ-b, 2 in AZ-c

C. 6 instances in AZ-a, 6 in AZ-b, 0 in AZ-c

D. 4 instances in AZ-a, 2 in AZ-b, 2 in AZ-c

E. 2 instances in AZ-a, 4 in AZ-b, 2 in AZ-c

## Correct Answer

**A. 3 instances in AZ-a, 3 in AZ-b, 3 in AZ-c**

**C. 6 instances in AZ-a, 6 in AZ-b, 0 in AZ-c**

## Explanation

Fault tolerance means maintaining 6 instances even if one AZ fails:
- **3+3+3**: If any AZ fails → 6 instances remain
- **6+6+0**: If any AZ fails → 6 instances remain

For 100% fault tolerance, remaining AZs must have ≥6 instances combined.

### Why other options are incorrect:

- **B** - 2+2+2=6, but if one AZ fails → only 4 instances remain.

- **D, E** - If the AZ with most instances fails → fewer than 6 remain.

## References

- https://media.amazonwebservices.com/AWS_Building_Fault_Tolerant_Applications.pdf
- https://tutorialsdojo.com/amazon-ec2/

## Domain

Design Resilient Architectures
