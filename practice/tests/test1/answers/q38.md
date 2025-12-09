# Question 38

A tech company has a CRM application hosted on an Auto Scaling group of On-Demand EC2 instances with different instance types and sizes. The application is extensively used during office hours from 9 in the morning to 5 in the afternoon. Their users are complaining that the performance of the application is slow during the start of the day but then works normally after a couple of hours.

Which of the following is the MOST operationally efficient solution to implement to ensure the application works properly at the beginning of the day?

## Options

A. Configure a Predictive scaling policy for the Auto Scaling group to automatically adjust the number of Amazon EC2 instances

B. Configure a Dynamic scaling policy for the Auto Scaling group to launch new instances based on the CPU utilization.

C. Configure a Dynamic scaling policy for the Auto Scaling group to launch new instances based on the Memory utilization.

D. Configure a Scheduled scaling policy for the Auto Scaling group to launch new instances before the start of the day.

## Correct Answer

**D. Configure a Scheduled scaling policy for the Auto Scaling group to launch new instances before the start of the day.**

## Explanation

Scaling based on a schedule allows you to scale your application in response to predictable load changes. Since you know the exact peak hours (9 AM to 5 PM), you can schedule scaling actions to launch instances before 9 AM.

The scheduled action tells Amazon EC2 Auto Scaling to perform a scaling action at specified times, ensuring instances are ready before the application is used.

### Why other options are incorrect:

- **B & C** - Dynamic scaling based on CPU or Memory reacts after the issue occurs. By the time metrics spike, performance is already affected.

- **A** - Predictive scaling assumes a homogenous Auto Scaling group. This scenario uses different instance types/sizes, making forecasts inaccurate.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/schedule_time.html
- https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-scheduled-scaling.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design High-Performing Architectures
