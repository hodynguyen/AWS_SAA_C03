# Question 28

A suite of web applications is hosted in an Auto Scaling group of Amazon EC2 instances across three Availability Zones and is configured with default settings. There is an Application Load Balancer that forwards the request to the respective target group on the URL path. The scale-in policy has been triggered due to the low number of incoming traffic to the application.

Which EC2 instance will be the first one to be terminated by the Auto Scaling group?

## Options

A. The EC2 instance which has been running for the longest time

B. The EC2 instance which has the least number of user sessions

C. The instance will be randomly selected by the Auto Scaling group

D. The EC2 instance launched from the oldest launch template.

## Correct Answer

**D. The EC2 instance launched from the oldest launch template.**

## Explanation

The default termination policy is designed to help ensure that your network architecture spans Availability Zones evenly. With the default termination policy, the behavior of the Auto Scaling group is as follows:

1. If there are instances in multiple Availability Zones, choose the Availability Zone with the most instances and at least one instance that is not protected from scale in. If there is more than one Availability Zone with this number of instances, choose the Availability Zone with the instances that use the oldest launch template.

2. Determine which unprotected instances in the selected Availability Zone use the oldest launch template. If there is one such instance, terminate it.

3. If there are multiple instances to terminate based on the above criteria, determine which unprotected instances are closest to the next billing hour.

4. If there is more than one unprotected instance closest to the next billing hour, choose one of these instances at random.

### Why other options are incorrect:

- **B** - The number of user sessions is not typically a factor considered by Amazon EC2 Auto Scaling groups when deciding which instances to terminate.

- **A** - The duration for which an EC2 instance has been running is not primarily a factor considered during scale-in events.

- **C** - Amazon EC2 Auto Scaling groups do not randomly select instances for termination during a scale-in event.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-termination.html#default-termination-policy
- https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-termination.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design Resilient Architectures
