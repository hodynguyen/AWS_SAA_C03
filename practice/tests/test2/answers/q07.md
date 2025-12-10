# Question 7

A music publishing company is building a multitier web application that requires a key-value store which will save the document models. Each model is composed of band ID, album ID, song ID, composer ID, lyrics, and other data. The web tier will be hosted in an Amazon ECS cluster with AWS Fargate launch type.

Which of the following is the MOST suitable setup for the database-tier?

## Options

A. Launch a DynamoDB table.

B. Launch an Amazon RDS database with Read Replicas.

C. Launch an Amazon Aurora Serverless database.

D. Use Amazon WorkDocs to store the document models.

## Correct Answer

**A. Launch a DynamoDB table.**

## Explanation

Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale. It is a fully managed cloud database and supports both document and key-value store models.

Its flexible data model, reliable performance, and automatic scaling of throughput capacity makes it a great fit for mobile, web, gaming, ad tech, IoT, and many other applications.

### Why other options are incorrect:

- **B** - RDS is relational, not suitable for key-value stores.

- **C** - Aurora Serverless is relational, not key-value.

- **D** - WorkDocs is for document sharing, not a database.

## References

- https://aws.amazon.com/dynamodb/
- https://tutorialsdojo.com/amazon-dynamodb/

## Domain

Design Resilient Architectures
