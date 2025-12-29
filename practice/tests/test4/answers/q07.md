# Question 7

An e-commerce company runs weekly sales promotions causing intermittent downtime. The application has long initialization times and only becomes operational minutes before EC2 instances reach RUNNING state. A solution is needed to launch capacity in advance based on forecasted load.

Which solution requires the least effort?

## Options

A. Use Amazon SageMaker Clarify to analyze and predict workload patterns. Create a scheduled scaling policy.

B. Create a dynamic scaling policy based on historical average CPU load.

C. Configure the Auto Scaling group to use predictive scaling.

D. Create a Scheduled EventBridge Rule that runs a scaling job on Lambda every midnight.

## Correct Answer

**C. Configure the Auto Scaling group to use predictive scaling.**

## Explanation

Predictive scaling uses machine learning to analyze historical CloudWatch data and forecast capacity requirements. It proactively launches instances before traffic spikes, solving the problem of long initialization times. This is built into Auto Scaling—no additional services needed.

### Why other options are incorrect:

- **A** - SageMaker Clarify detects ML model bias, not traffic patterns. This adds unnecessary complexity.

- **B** - Dynamic scaling is reactive—it responds after thresholds are breached, not before.

- **D** - Requires manual implementation and adjustments when promotion schedules change.

## References

- https://docs.aws.amazon.com/autoscaling/plans/userguide/how-it-works.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design Resilient Architectures
