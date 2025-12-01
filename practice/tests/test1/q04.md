# Question 4

An online shopping platform is hosted on an Auto Scaling group of Amazon EC2 Spot instances and utilizes Amazon Aurora PostgreSQL as its database. It is required to optimize database workloads in the cluster by directing the production traffic to high-capacity instances and routing the reporting queries from the internal staff to the low-capacity instances.

Which is the most suitable configuration for the application as well as the Aurora database cluster to achieve this requirement?

## Options

A. Do nothing since by default, Aurora will automatically direct the production traffic to your high-capacity instances and the reporting queries to your low-capacity instances.

B. In your application, use the instance endpoint of your Aurora database to handle the incoming production traffic and use the cluster endpoint to handle reporting queries.

C. Configure your application to use the reader endpoint for both production traffic and reporting queries, which will enable your Aurora database to automatically perform load-balancing among all the Aurora Replicas.

D. Create a custom endpoint in Aurora based on the specified criteria for the production traffic and another custom endpoint to handle the reporting queries.

## Correct Answer

**D. Create a custom endpoint in Aurora based on the specified criteria for the production traffic and another custom endpoint to handle the reporting queries.**

## Explanation

Amazon Aurora typically involves a cluster of DB instances instead of a single instance. Each connection is handled by a specific DB instance. When you connect to an Aurora cluster, the host name and port that you specify point to an intermediate handler called an endpoint.

Using endpoints, you can map each connection to the appropriate instance or group of instances based on your use case. The custom endpoint provides load-balanced database connections based on criteria other than the read-only or read-write capability of the DB instances.

For example, you might define a custom endpoint to connect to instances that use a particular AWS instance class or a particular DB parameter group. Then you might direct internal users to low-capacity instances for report generation or ad hoc querying, and direct production traffic to high-capacity instances.

### Why other options are incorrect:

- **C** - Although a reader endpoint enables your Aurora database to automatically perform load-balancing among all the Aurora Replicas, it is quite limited to doing read operations only. You still need to use a custom endpoint to load-balance the database connections based on the specified criteria.

- **B** - A cluster endpoint (also known as a writer endpoint) simply connects to the current primary DB instance. It does not point to lower-capacity or high-capacity instances as per the requirement.

- **A** - Aurora does not do this by default. You have to create custom endpoints in order to accomplish this requirement.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.Endpoints.html
- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Endpoints.Custom.html
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design Resilient Architectures
