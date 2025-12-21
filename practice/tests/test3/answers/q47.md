# Question 47

## Topic
Design High-Performing Architectures

## Question
A company deployed an on-premises application that uses a MySQL database. The company is migrating the application to AWS and wants to use Amazon Aurora MySQL to redesign the database. A Solutions Architect must ensure that the migrated application can achieve strong consistency for reads made immediately after a write.

Which approach should the Solutions Architect take?

## Options
A. Use the Amazon Aurora Serverless v2 endpoint to read from the primary instance.

B. Set up Amazon Aurora replicas with cross-Region replication and use the read endpoint.

C. Enable read replicas and use Aurora's reader endpoint for read queries.

D. Configure the application to use the cluster endpoint for write operations and for read operations immediately after the write.

## Correct Answer
D

## Explanation
Amazon Aurora's cluster endpoint points to the primary DB instance, which can handle both read and write operations. Using the cluster endpoint for reads immediately after writes ensures strong consistency because you're reading from the same instance that handled the write.

The reader endpoint routes connections to available Aurora replicas, which may have replication lag, potentially causing inconsistent reads immediately after writes.

**Why other options are incorrect:**
- **Option A** is incorrect because Aurora Serverless v2 endpoint alone doesn't guarantee strong consistency for immediate reads.
- **Option B** is incorrect because cross-Region replicas have replication lag.
- **Option C** is incorrect because reader endpoints route to replicas which may have replication lag.

## References
- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.Endpoints.html
- https://tutorialsdojo.com/amazon-aurora/
