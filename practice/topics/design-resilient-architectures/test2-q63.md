# Question 63

A company runs a web application on Amazon EC2 instances in an Auto Scaling group. The company notices that the instances are frequently scaling up and down rapidly.

Which action will stabilize the scaling behavior?

## Options

A. Increase the cooldown period.

B. Decrease the minimum instance count.

C. Enable detailed monitoring.

D. Change from target tracking to simple scaling.

## Correct Answer

**A. Increase the cooldown period.**

## Explanation

The cooldown period prevents Auto Scaling from launching or terminating additional instances before the previous scaling activity takes effect. Increasing it reduces rapid scaling (thrashing).

### Why other options are incorrect:

- **B** - Decreasing minimum instances doesn't stabilize scaling.

- **C** - Detailed monitoring provides more data but doesn't stabilize.

- **D** - Simple scaling is less responsive than target tracking.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/Cooldown.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design Resilient Architectures
