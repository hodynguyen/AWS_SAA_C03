# Question 62

An application requires 6 EC2 instances minimum and must be fault-tolerant to one AZ failure. The solution must be cost-effective.

What is the most cost-effective deployment across 3 AZs?

## Options

A. 6 instances in each of 3 AZs (18 total)

B. 6 instances in 2 AZs, 0 in third (12 total)

C. 3 instances in each of 3 AZs (9 total)

D. 2 instances in each of 3 AZs (6 total)

## Correct Answer

**C. 3 instances in each of 3 AZs (9 total)**

## Explanation

Fault tolerance with minimum cost:
- **3+3+3 = 9 instances**: If one AZ fails → 6 remain ✓
- Meets requirement with fewest total instances

### Why other options are incorrect:

- **A** - 18 instances is overkill and expensive.

- **B** - 12 instances works but costs more than 9.

- **D** - 2+2+2 = 6: If one AZ fails → only 4 remain (doesn't meet requirement).

## References

- https://media.amazonwebservices.com/AWS_Building_Fault_Tolerant_Applications.pdf
- https://tutorialsdojo.com/amazon-ec2/

## Domain

Design Cost-Optimized Architectures
