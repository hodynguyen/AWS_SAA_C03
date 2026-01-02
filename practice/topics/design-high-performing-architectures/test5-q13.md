# Question 13

An Auto Scaling group is scaling up and down multiple times per hour.

What design change optimizes cost while preserving elasticity?

## Options

A. Upgrade instance type in launch template.

B. Add provisioned IOPS to instances.

C. Increase base number of Auto Scaling instances.

D. Change cooldown period and set CloudWatch metric to higher threshold.

## Correct Answer

**D. Change cooldown period and set CloudWatch metric to higher threshold.**

## Explanation

Frequent scaling indicates:
- **Cooldown too short**: Not waiting for previous scaling to take effect
- **Threshold too sensitive**: Triggering on small variations

Increasing cooldown prevents premature scaling; higher threshold reduces false triggers.

### Why other options are incorrect:

- **A** - Larger instances cost more, doesn't address scaling frequency.

- **B** - Provisioned IOPS adds cost, unrelated to scaling behavior.

- **C** - More base instances costs more, not cost optimization.

## References

- http://docs.aws.amazon.com/autoscaling/latest/userguide/as-scale-based-on-demand.html
- https://tutorialsdojo.com/amazon-ec2-auto-scaling/

## Domain

Design High-Performing Architectures
