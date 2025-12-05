# Question 39

A company hosted a web application in an Auto Scaling group of EC2 instances. The IT manager is concerned about the over-provisioning of the resources that can cause higher operating costs. A Solutions Architect has been instructed to create a cost-effective solution without affecting the performance of the application.

Which dynamic scaling policy should be used to satisfy this requirement?

## Options

A. Use suspend and resume scaling.

B. Use target tracking scaling.

C. Use scheduled scaling.

D. Use simple scaling.

## Correct Answer

**B. Use target tracking scaling.**

## Explanation

With a target tracking scaling policy, you can increase or decrease the current capacity of the group based on a target value for a specific metric. This policy will help resolve the over-provisioning of your resources.

The scaling policy adds or removes capacity as required to keep the metric at, or close to, the specified target value. It also adjusts to changes in the metric due to a changing load pattern.

### Why other options are incorrect:

- **D** - Simple scaling requires waiting for cooldown periods before responding to additional alarms.

- **C** - Scheduled scaling is for predictable traffic patterns, not for optimizing cost based on current load.

- **A** - Suspend and resume scaling is used to temporarily pause scaling activities.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-target-tracking.html
- https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design Cost-Optimized Architectures
