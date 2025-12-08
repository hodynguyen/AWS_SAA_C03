# Question 57

A retail company receives raw .csv data files into its Amazon S3 bucket from multiple sources on an hourly basis, with an average file size of 2 GB.

An automated process must be implemented to convert these .csv files into the more efficient Apache Parquet format and store the converted files in another S3 bucket. Additionally, the conversion process must be automatically initiated each time a new file is uploaded into the S3 bucket.

Which of the following options must be implemented to meet these requirements with the LEAST operational overhead?

## Options

A. Set up an Apache Spark job running in an Amazon EC2 instance and create an Amazon EventBridge rule to monitor S3 PUT events.

B. Create an ETL (Extract, Transform, Load) job and a Data Catalog table in AWS Glue. Configure the Glue crawler to run on a schedule every hour.

C. Use an AWS Lambda function triggered by an S3 PUT event to convert the .csv files to Parquet format.

D. Utilize an AWS Glue extract, transform, and load (ETL) job to process and convert the .csv files to Apache Parquet format. Set up an S3 Event Notification to track every S3 PUT event and invoke the ETL job in Glue through Amazon SQS.

## Correct Answer

**D. Utilize an AWS Glue extract, transform, and load (ETL) job to process and convert the .csv files to Apache Parquet format and then store the output files into the target S3 bucket. Set up an S3 Event Notification to track every S3 PUT event and invoke the ETL job in Glue through Amazon SQS.**

## Explanation

AWS Glue is a powerful ETL service for data transformation. Using S3 event notifications to trigger the Glue job via SQS ensures immediate processing when new files are uploaded.

Apache Parquet is a columnar storage format that provides higher efficiency for big data processing.

### Why other options are incorrect:

- **C** - Lambda has execution time limits and memory limits. Not efficient for 2GB files.

- **A** - Running Spark on EC2 requires manual provisioning and maintenance.

- **B** - Scheduled hourly runs aren't as immediate as event-triggered processing.

## References

- https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-etl-format-parquet-home.html
- https://aws.amazon.com/blogs/big-data/run-aws-glue-crawlers-using-amazon-s3-event-notifications/
- https://tutorialsdojo.com/aws-glue/

## Domain

Design High-Performing Architectures
