# Question 65

Financial calculations nightly 10PM-3AM. Need reserved capacity in specific AZ. Cost-effective solution.

## Options

A. Regional Reserved Instances.

B. Dedicated Hosts.

C. On-Demand EC2.

D. On-Demand Capacity Reservations.

## Correct Answer

**D. On-Demand Capacity Reservations.**

## Explanation

Capacity Reservations for scheduled workloads:
- **Specific AZ**: Guaranteed capacity
- **Any duration**: No 1-3 year commitment
- **Cancel anytime**: Stop paying when done
- **Combine with Savings Plans**: For discounts

### Why other options are incorrect:

- **A** - Regional RIs don't reserve specific AZ capacity.

- **B** - Dedicated Hosts are expensive for 5-hour use.

- **C** - On-Demand can't reserve capacity.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Cost-Optimized Architectures
