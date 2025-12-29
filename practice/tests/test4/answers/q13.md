# Question 13

A Solutions Architect needs to monitor RDS database metrics in CloudWatch for an enrollment system.

What are the Enhanced Monitoring metrics that provide more accurate information? (Select TWO.)

## Options

A. OS processes

B. Database Connections

C. CPU Utilization

D. RDS child processes

E. Freeable Memory

## Correct Answer

**A. OS processes**

**D. RDS child processes**

## Explanation

Enhanced Monitoring collects metrics from an agent running on the DB instance, providing OS-level visibility. The metrics include:
- **RDS child processes**: Shows resource usage of database processes (e.g., mysqld, aurora)
- **OS processes**: Shows kernel and system process summaries

Standard CloudWatch metrics (CPU Utilization, Database Connections, Freeable Memory) come from the hypervisor, not the instance itself.

### Why other options are incorrect:

- **B, C, E** - Database Connections, CPU Utilization, and Freeable Memory are standard RDS CloudWatch metrics, not Enhanced Monitoring metrics.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html
- https://tutorialsdojo.com/amazon-cloudwatch/

## Domain

Design Resilient Architectures
