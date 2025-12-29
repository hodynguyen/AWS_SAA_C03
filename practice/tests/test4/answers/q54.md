# Question 54

An Auto Scaling group of EC2 instances has high memory usage, but ASG is not launching more instances. Basic CloudWatch monitoring is enabled.

What should be implemented to solve this issue?

## Options

A. Install CloudWatch unified agent. Create custom metric for memory usage. Scale ASG based on aggregated metric.

B. Use Amazon Rekognition and Well-Architected Tool to trigger scale-out.

C. Enable detailed monitoring. Use Auto Scaling with custom metrics.

D. Use Amazon Comprehend and SageMaker to trigger Auto Scaling.

## Correct Answer

**A. Install CloudWatch unified agent. Create custom metric for memory usage. Scale ASG based on aggregated metric.**

## Explanation

By default, CloudWatch doesn't monitor memory usage—only CPU, network, and disk. To scale based on memory:
1. **Install CloudWatch agent**: Collects memory metrics from instances
2. **Store config in Parameter Store**: Centralized agent configuration
3. **Create scaling policy**: Use custom memory metric as trigger

### Why other options are incorrect:

- **B** - Rekognition is for image recognition; Well-Architected Tool is for best practice reviews.

- **C** - Detailed monitoring increases metric granularity but doesn't add memory metrics.

- **D** - Comprehend is for NLP; SageMaker is for ML, not instance monitoring.

## References

- https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Install-CloudWatch-Agent.html
- https://tutorialsdojo.com/amazon-cloudwatch/

## Domain

Design High-Performing Architectures
