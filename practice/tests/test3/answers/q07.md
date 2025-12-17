# Question 7

## Topic
Design High-Performing Architectures

## Question
A firm has a containerized application that runs on a self-managed Kubernetes cluster. The cluster writes data in an on-premises MongoDB database. A solutions architect is requested to move the service to AWS in order to minimize operational overhead. The firm prohibits any changes to the code.

Which action meets these objectives?

## Options
A. Migrate the cluster to an Amazon Elastic Container Service (ECS) cluster with the images stored in the Amazon Elastic Container Registry (Amazon ECR). Move the database to an Amazon Neptune database.

B. Migrate the cluster to an Amazon Elastic Kubernetes Service (EKS) cluster and the database to an Amazon DocumentDB (with MongoDB compatibility) database.

C. Migrate the cluster to an Amazon Elastic Container Service (ECS) cluster using Amazon ECS Anywhere and the database to an Amazon Aurora Serverless database.

D. Migrate the cluster to an Amazon Elastic Kubernetes Service (EKS) cluster using Amazon EKS Anywhere and the database to an Amazon DynamoDB table.

## Correct Answer
B

## Explanation
Amazon DocumentDB (with MongoDB compatibility) is a fast, scalable, highly available, and fully managed document database service that supports MongoDB workloads. Since the firm prohibits any code changes, using Amazon DocumentDB is the best choice as it is compatible with MongoDB.

Amazon EKS is the managed Kubernetes service that can run the existing containerized application without modifications.

**Why other options are incorrect:**
- **Option A** is incorrect because Amazon Neptune is a graph database, not suitable for MongoDB workloads.
- **Option C** is incorrect because Amazon Aurora is a relational database, not compatible with MongoDB.
- **Option D** is incorrect because migrating to DynamoDB would require code changes since DynamoDB has different APIs than MongoDB.

## References
- https://docs.aws.amazon.com/documentdb/latest/developerguide/docdb-migration.html
- https://aws.amazon.com/eks/
- https://tutorialsdojo.com/amazon-documentdb/
