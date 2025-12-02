# Question 14

A company has a highly available architecture consisting of an Elastic Load Balancer and multiple Amazon EC2 instances configured with Auto Scaling across three Availability Zones. The company needs to monitor EC2 instances based on a specific metric that is not readily available in Amazon CloudWatch.

Which of the following is a custom metric in CloudWatch that requires manual setup?

## Options

A. CPU Utilization of an EC2 instance

B. Disk Read activity of an EC2 instance

C. Memory Utilization of an EC2 instance

D. Network packets out of an EC2 instance

## Correct Answer

**C. Memory Utilization of an EC2 instance**

## Explanation

Amazon CloudWatch has Amazon EC2 Metrics available for monitoring. CPU Utilization identifies the processing power required to run an application. Network Utilization identifies the volume of incoming and outgoing network traffic. The Disk Read metric is used to determine the volume of data the application reads from the hard disk.

However, there are certain metrics that are not readily available in CloudWatch which can be collected by setting up a custom metric. You need to prepare a custom metric using CloudWatch Monitoring Scripts or install CloudWatch Agent.

Here's the list of some of the custom metrics that you can set up:
- Memory utilization
- Disk swap utilization
- Disk space utilization
- Page file utilization
- Log collection

### Why other options are incorrect:

- **A** - CPU Utilization is available by default in CloudWatch.

- **B** - Disk read activity is already included in CloudWatch.

- **D** - Network packets out is included in CloudWatch's default network utilization monitoring.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring_ec2.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/mon-scripts.html#using_put_script
- https://tutorialsdojo.com/amazon-cloudwatch/

## Domain

Design High-Performing Architectures
