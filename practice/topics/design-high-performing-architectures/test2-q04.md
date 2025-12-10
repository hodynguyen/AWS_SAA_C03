# Question 4

A company receives semi-structured and structured data from different sources, which are eventually stored in their Amazon S3 data lake. The Solutions Architect plans to use big data processing frameworks to analyze these data and access it using various business intelligence tools and standard SQL queries.

Which of the following provides the MOST high-performing solution that fulfills this requirement?

## Options

A. Create an Amazon EMR cluster and store the processed data in Amazon Redshift.

B. Use AWS Glue and store the processed data in Amazon S3.

C. Create an Amazon EC2 instance and store the processed data in Amazon EBS.

D. Use Amazon Managed Service for Apache Flink Studio and store the processed data in Amazon DynamoDB.

## Correct Answer

**A. Create an Amazon EMR cluster and store the processed data in Amazon Redshift.**

## Explanation

Amazon EMR is a managed cluster platform that simplifies running big data frameworks, such as Apache Hadoop and Apache Spark, on AWS to process and analyze vast amounts of data.

Amazon Redshift is the most widely used cloud data warehouse. It allows you to run complex analytic queries against terabytes to petabytes of structured and semi-structured data.

The combination of EMR for processing and Redshift for analytics provides the most high-performing solution.

### Why other options are incorrect:

- **B** - Glue + S3 lacks the SQL querying power of Redshift for BI tools.

- **C** - Single EC2 with EBS is limited and requires manual management.

- **D** - Apache Flink is for streaming data; DynamoDB doesn't support complex SQL.

## References

- https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html
- https://tutorialsdojo.com/amazon-emr/

## Domain

Design High-Performing Architectures
