# Question 62

ASG app has morning traffic bursts with timeouts. EC2 takes 1 minute to boot.

How should the architecture be redesigned?

## Options

A. Create step scaling with instance warm-up time.

B. Create NLB with slow-start mode.

C. Create CloudFront with EC2 origin.

D. Create new launch template with larger instance.

## Correct Answer

**A. Create step scaling with instance warm-up time.**

## Explanation

Step scaling with warm-up:
- **Warm-up time**: Excludes new instances from scaling metrics
- **Prevents premature scaling**: Waits for instance to be ready
- **Step adjustments**: Scale based on alarm breach size

### Why other options are incorrect:

- **B** - NLB doesn't support slow-start mode (ALB does).

- **C** - CloudFront helps latency, not instance boot time.

- **D** - Larger instance doesn't improve boot time.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-simple-step.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design Resilient Architectures
