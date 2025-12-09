# Question 20

An e-commerce company runs a highly scalable web application that depends on an Amazon Aurora database. As the number of users increases, the read replica faces difficulties keeping up with the increasing read traffic, causing performance bottlenecks during peak periods.

Which of the following will resolve the issue with the most cost-effective solution?

## Options

A. Increase the size of the Aurora DB cluster.

B. Implement read scaling with Aurora Global Database.

C. Set up a read replica that can operate across different regions.

D. Use automatic scaling for the Aurora read replica using Aurora Auto Scaling.

## Correct Answer

**D. Use automatic scaling for the Aurora read replica using Aurora Auto Scaling.**

## Explanation

Amazon Aurora is a cloud-based relational database service that provides better performance and reliability for database workloads. One of the key features of Amazon Aurora is Aurora Auto Scaling, which automatically adjusts the capacity of your Aurora database cluster based on the workload.

Aurora Auto Scaling is particularly useful for businesses that have fluctuating workloads. It ensures that your database cluster scales up or down as needed without manual intervention. This feature saves time and resources, allowing businesses to focus on other aspects of their operations.

In this scenario, the company can benefit from using Aurora Auto Scaling. This solution allows the system to dynamically manage resources, effectively addressing the surge in read traffic during peak periods.

### Why other options are incorrect:

- **A** - It's not economical to upsize the cluster just to alleviate the bottleneck during peak periods. A static increase results in constant costs regardless of utilization.

- **B** - Amazon Aurora Global Database is primarily designed for globally distributed applications. It introduces additional complexity and can be more expensive.

- **C** - Setting up a cross-region read replica incurs additional costs for inter-region data replication. The issue is not related to cross-region availability but rather performance within the current region.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Integrating.AutoScaling.html
- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design High-Performing Architectures
