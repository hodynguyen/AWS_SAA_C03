# Question 32

## Topic
Design High-Performing Architectures

## Question
A company has an OLTP (Online Transactional Processing) application that is hosted in an Amazon ECS cluster using the Fargate launch type. It has an Amazon RDS database that stores data of its production website. The Data Analytics team needs to run queries against the database to track and audit all user transactions. These query operations against the production database must not impact application performance in any way.

Which of the following is the MOST suitable and cost-effective solution that you should implement?

## Options
A. Upgrade the instance type of the RDS database to a large instance.

B. Set up a new Amazon RDS Read Replica of the production database. Direct the Data Analytics team to query the production data from the replica.

C. Set up a Multi-AZ deployments configuration of your production database in RDS. Direct the Data Analytics team to query the production data from the standby instance.

D. Set up a new Amazon Redshift database cluster. Migrate the product database into Redshift and allow the Data Analytics team to fetch data from it.

## Correct Answer
B

## Explanation
Amazon RDS Read Replicas provide enhanced performance and durability for database (DB) instances. This feature makes it easy to elastically scale out beyond the capacity constraints of a single DB instance for read-heavy database workloads.

You can create one or more replicas of a given source DB Instance and serve high-volume application read traffic from multiple copies of your data, thereby increasing aggregate read throughput. Read replicas can also be promoted when needed to become standalone DB instances. Read replicas are available in Amazon RDS for MySQL, MariaDB, Oracle and PostgreSQL, as well as Amazon Aurora.

You can reduce the load on your source DB instance by routing read queries from your applications to the read replica. These replicas allow you to elastically scale out beyond the capacity constraints of a single DB instance for read-heavy database workloads.

Because read replicas can be promoted to master status, they are useful as part of a sharding implementation. To shard your database, add a read replica and promote it to master status, then, from each of the resulting DB Instances, delete the data that belongs to the other shard.

Hence, the correct answer is: Set up a new Amazon RDS Read Replica of the production database. Direct the Data Analytics team to query the production data from the replica.

References:

https://aws.amazon.com/caching/database-caching/

https://aws.amazon.com/rds/details/read-replicas/

https://aws.amazon.com/elasticache/

Check out this Amazon RDS Cheat Sheet:

https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

**Why other options are incorrect:**

- The option that says: Set up a new Amazon Redshift database cluster. Migrate the product database into Redshift and allow the Data Analytics team to fetch data from it is incorrect because Redshift is primarily used for OLAP (Online Analytical Processing) applications and not for OLTP.

- The option that says: Set up a Multi-AZ deployments configuration of your production database in RDS. Direct the Data Analytics team to query the production data from the standby instance is incorrect because you can't directly connect to the standby instance. This is only used in the event of a database failover when your primary instance encountered an outage.

- The option that says: Upgrade the instance type of the RDS database to a large instance is incorrect because this entails a significant amount of cost. Moreover, the production database could still be affected by the queries done by the Data Analytics team. A better solution for this scenario is to use a Read Replica instead.

