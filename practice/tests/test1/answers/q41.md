# Question 41

A company has a cloud architecture composed of Linux and Windows Amazon EC2 instances that process high volumes of financial data 24 hours a day, 7 days a week. To ensure high availability of the systems, the Solutions Architect must create a solution that enables monitoring of memory and disk utilization metrics for all instances.

Which of the following is the most suitable monitoring solution to implement?

## Options

A. Use the default Amazon CloudWatch configuration to EC2 instances where the memory and disk utilization metrics are already available.

B. Enable the Enhanced Monitoring option in EC2 and install Amazon CloudWatch agent to all the EC2 instances.

C. Use Amazon Inspector and install the Inspector agent to all EC2 instances.

D. Install the Amazon CloudWatch agent to all the EC2 instances that gather the memory and disk utilization data. View the custom metrics in the CloudWatch console.

## Correct Answer

**D. Install the Amazon CloudWatch agent to all the EC2 instances that gather the memory and disk utilization data. View the custom metrics in the CloudWatch console.**

## Explanation

By default, CloudWatch does not automatically provide memory and disk utilization metrics. You need to set up custom CloudWatch metrics using the CloudWatch agent to monitor memory, disk swap, disk space, and page file utilization.

The multi-platform CloudWatch agent can be installed on both Linux and Windows-based instances and supports selecting metrics to be collected, including sub-resource metrics such as per-CPU core.

### Why other options are incorrect:

- **A** - By default, CloudWatch does not provide memory and disk utilization metrics.

- **B** - Enhanced Monitoring is only a feature of Amazon RDS, not EC2.

- **C** - Amazon Inspector is for security assessment, not for monitoring memory/disk utilization.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring_ec2.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/mon-scripts.html
- https://tutorialsdojo.com/amazon-cloudwatch/

## Domain

Design Resilient Architectures
