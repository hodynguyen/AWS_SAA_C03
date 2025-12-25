# Question 25

## Topic
Design Resilient Architectures

## Question
A Solutions Architect is designing a setup for a database that will run on Amazon RDS for MySQL. He needs to ensure that the database can automatically failover to an RDS instance to continue operating in the event of failure. The architecture should also be as highly available as possible.

Which among the following actions should the Solutions Architect do?

## Options
A. Create a standby replica in another availability zone by enabling Multi-AZ deployment.

B. Create five read replicas across different availability zones. In the event of an Availability Zone outage, promote any replica to become the primary instance.

C. Create five cross-region read replicas in each region. In the event of an Availability Zone outage, promote any replica to become the primary instance.

D. Create a read replica in the same region where the DB instance resides. In addition, create a read replica in a different region to survive a region’s failure. In the event of an Availability Zone outage, promote any replica to become the primary instance.

## Correct Answer
A

## Explanation
You can run an Amazon RDS DB instance in several AZs with Multi-AZ deployment. Amazon automatically provisions and maintains a secondary standby DB instance in a different AZ. Your primary DB instance is synchronously replicated across AZs to the secondary instance to provide data redundancy, failover support, eliminate I/O freezes, and minimize latency spikes during systems backup.

As described in the scenario, the architecture must meet two requirements:

The database should automatically fail over to an RDS instance in case of failures.

The architecture should be as highly available as possible.

Hence, the correct answer is: Create a standby replica in another availability zone by enabling Multi-AZ deployment because it meets both of the requirements.

Both the following options are incorrect:

- Create five read replicas across different availability zones. In the event of an Availability Zone outage, promote any replica to become the primary instance

- Create five cross-region read replicas in each region. In the event of an Availability Zone outage, promote any replica to become the primary instance

Although it is possible to achieve high availability with these architectures by promoting a read replica into the primary instance in an event of failure, it does not support automatic failover to an RDS instance which is also a requirement in the problem.

References:

https://aws.amazon.com/rds/features/multi-az/

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html

Check out this Amazon RDS Cheat Sheet:

https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

**Why other options are incorrect:**

- The option that says: Create a read replica in the same region where the DB instance resides. In addition, create a read replica in a different region to survive a region's failure. In the event of an Availability Zone outage, promote any replica to become the primary instance is incorrect. Although this architecture provides higher availability since it can survive a region failure, it still does not meet the first requirement since the process is not automated. The architecture should also support automatic failover to an RDS instance in case of failures.

