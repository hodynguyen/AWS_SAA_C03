# Question 27

An online cryptocurrency exchange platform is hosted in AWS, utilizing an Amazon ECS Cluster and Amazon RDS in a Multi-AZ Deployments configuration. The application heavily uses the RDS instance to process complex read and write database operations. To maintain reliability, availability, and performance, it is necessary to closely monitor how the different processes or threads on a DB instance use the CPU, including the percentage of CPU bandwidth and total memory consumed by each process.

Which of the following is the most suitable solution to monitor the database properly?

## Options

A. Create a script that collects and publishes custom metrics to Amazon CloudWatch, which tracks the real-time CPU Utilization of the RDS instance, and then set up a custom CloudWatch dashboard to view the metrics.

B. Use Amazon CloudWatch to monitor the CPU Utilization of your database.

C. Check the CPU% and MEM% metrics which are readily available in the RDS console that shows the percentage of the CPU bandwidth and total memory consumed by each database process of your RDS instance.

D. Enable Enhanced Monitoring in RDS.

## Correct Answer

**D. Enable Enhanced Monitoring in RDS.**

## Explanation

Amazon RDS offers a powerful feature known as Enhanced Monitoring, which provides detailed metrics in real-time about the operating system (OS) underlying your database instances. This feature allows users to monitor performance at a granular level through the AWS Management Console or by accessing the Enhanced Monitoring JSON output via CloudWatch Logs.

Enhanced Monitoring differs from standard CloudWatch metrics in that it gathers data directly from an agent installed on the instance, rather than from the hypervisor, which is used by CloudWatch. This distinction can lead to slight variations between the two sets of metrics.

This feature is particularly beneficial for users who need in-depth visibility into how individual processes or threads on a DB instance utilize CPU resources.

### Why other options are incorrect:

- **B** - Although you can use CloudWatch to monitor CPU Utilization, it does not provide the percentage of CPU bandwidth and total memory consumed by each database process. CloudWatch primarily gathers metrics from the hypervisor.

- **A** - CloudWatch alone is not enough to get the specific percentage of CPU bandwidth and total memory consumed by each database process. You don't have direct access to RDS instances like EC2 instances.

- **C** - The CPU% and MEM% metrics are not readily available in the Amazon RDS console, which is contrary to what is stated in this option.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html
- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/MonitoringOverview.html
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Resilient Architectures
