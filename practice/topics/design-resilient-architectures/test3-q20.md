# Question 20

## Topic
Design Resilient Architectures

## Question
An online registration system hosted in an Amazon EKS cluster stores data to a db.t4g.medium Amazon Aurora DB cluster. The database performs well during regular hours but is unable to handle the traffic surge that occurs during flash sales. A solutions architect must move the database to Aurora Serverless while minimizing downtime and the impact on the operation of the application.

Which change should be taken to meet the objective?

## Options
A. Add an Aurora Replica to the cluster and set its instance class to Serverless. Failover to the read replica and promote it to primary.

B. Change the Aurora Instance class to Serverless

C. Use AWS Database Migration Service (AWS DMS) to migrate to a new Aurora Serverless database.

D. Take a snapshot of the DB cluster. Use the snapshot to create a new Aurora DB cluster.

## Correct Answer
C

## Explanation
AWS Database Migration Service helps you migrate your databases to AWS with virtually no downtime. All data changes to the source database that occur during the migration are continuously replicated to the target, allowing the source database to be fully operational during the migration process.

You can set up a DMS task for ongoing replication that keeps your source and target databases in sync.

**Why other options are incorrect:**
- **Option A** is incorrect because you cannot set the instance class from Provisioned to Serverless for a replica.
- **Option B** is incorrect because changing the instance class from Provisioned to Serverless is not possible directly.
- **Option D** is incorrect because this involves a long period of downtime since you have to stop the application until the new cluster is created.

## References
- https://aws.amazon.com/dms/
- https://aws.amazon.com/rds/aurora/faqs
- https://tutorialsdojo.com/aws-database-migration-service/
