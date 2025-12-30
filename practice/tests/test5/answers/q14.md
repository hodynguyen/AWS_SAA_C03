# Question 14

A Docker-based batch application processes both mission-critical and non-essential jobs.

What is the most cost-effective implementation?

## Options

A. ECS with Reserved EC2 for both workloads.

B. ECS with Spot EC2 for both workloads.

C. ECS with Reserved EC2 for mission-critical, Spot for non-essential.

D. ECS with On-Demand EC2 for both workloads.

## Correct Answer

**C. ECS with Reserved EC2 for mission-critical, Spot for non-essential.**

## Explanation

Optimal cost strategy:
- **Reserved Instances**: Guaranteed capacity for mission-critical (up to 72% savings)
- **Spot Instances**: Cheapest for interruptible non-essential work (up to 90% savings)

Mix both to balance reliability and cost.

### Why other options are incorrect:

- **A** - Reserved for everything is more expensive than using Spot for non-essential.

- **B** - Spot for mission-critical is risky; AWS can terminate anytime.

- **D** - On-Demand is most expensive option.

## References

- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html
- https://tutorialsdojo.com/amazon-elastic-container-service-amazon-ecs/

## Domain

Design Resilient Architectures
