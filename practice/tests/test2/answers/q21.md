# Question 21

A commercial bank has a forex trading application. They created an Auto Scaling group of EC2 instances that allow the bank to cope with the current traffic and achieve cost-efficiency. They want the Auto Scaling group to behave in such a way that it will follow a predefined set of parameters before it scales down the number of EC2 instances, which protects the system from unintended slowdown or unavailability.

Which of the following statements are true regarding the cooldown period? (Select TWO.)

## Options

A. It ensures that the Auto Scaling group launches or terminates additional EC2 instances without any downtime.

B. Its default value is 300 seconds.

C. It ensures that before the Auto Scaling group scales out, the EC2 instances have ample time to cooldown.

D. Its default value is 600 seconds.

E. It ensures that the Auto Scaling group does not launch or terminate additional EC2 instances before the previous scaling activity takes effect.

## Correct Answers

**B. Its default value is 300 seconds.**

**E. It ensures that the Auto Scaling group does not launch or terminate additional EC2 instances before the previous scaling activity takes effect.**

## Explanation

The cooldown period is a configurable setting that helps ensure Auto Scaling doesn't launch or terminate additional instances before the previous scaling activity takes effect.

Default cooldown period is 300 seconds (5 minutes).

### Why other options are incorrect:

- **A, C** - These don't accurately describe cooldown behavior.

- **D** - Default is 300 seconds, not 600.

## References

- http://docs.aws.amazon.com/autoscaling/latest/userguide/as-instance-termination.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design Resilient Architectures
