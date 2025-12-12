# Question 19

A company hosts its web application on a set of Amazon EC2 instances in an Auto Scaling group behind an Application Load Balancer (ALB). The application has an embedded NoSQL database. As the application receives more traffic, the application becomes overloaded mainly due to database requests.

Which of the following options can meet the company requirements with the least operational overhead?

## Options

A. Configure the Auto Scaling group to spread the EC2 instances across three Availability Zones. Configure replication of the NoSQL database on the set of EC2 instances to spread the database load.

B. Change the ALB with a Network Load Balancer (NLB) to handle more traffic. Use the AWS Glue DynamoDB export connector to export data from Amazon DynamoDB to Amazon S3 for analytics periodically.

C. Configure the Auto Scaling group to spread the EC2 instances across three Availability Zones. Use the AWS Database Migration Service (AWS DMS) with a replication server and an ongoing replication task to migrate the embedded NoSQL database to Amazon DynamoDB.

D. Change the ALB with a Network Load Balancer (NLB) to handle more traffic and integrate AWS Global Accelerator to ensure high availability.

## Correct Answer

**C. Configure the Auto Scaling group to spread the EC2 instances across three Availability Zones. Use the AWS Database Migration Service (AWS DMS) with a replication server and an ongoing replication task to migrate the embedded NoSQL database to Amazon DynamoDB.**

## Explanation

AWS DMS makes it easy to migrate databases to AWS with minimal downtime. Migrating to Amazon DynamoDB provides a managed, highly available NoSQL database with low operational overhead.

### Why other options are incorrect:

- **A** - Running embedded database on EC2 requires manual management.

- **B, D** - These don't address the database scalability issue.

## References

- https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Target.DynamoDB.html
- https://tutorialsdojo.com/aws-database-migration-service/

## Domain

Design Resilient Architectures
