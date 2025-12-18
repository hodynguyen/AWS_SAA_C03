# Question 14

## Topic
Design High-Performing Architectures

## Question
A data analytics company is setting up an innovative checkout-free grocery store. The Solutions Architect developed a real-time monitoring application that uses smart sensors to collect the items that the customers are getting from the grocery's refrigerators and shelves, then automatically deduct those items from customer accounts. The company wants to analyze the items that are frequently being bought and store the results in Amazon S3 for durable storage to determine the purchase behavior of its customers.

Which of the following must be used to easily capture, transform, and load streaming data into S3, Amazon OpenSearch Service, and Splunk?

## Options
A. Amazon DynamoDB Streams

B. Amazon SQS

C. Amazon Redshift

D. Amazon Data Firehose

## Correct Answer
D

## Explanation
Amazon Data Firehose is the easiest way to load streaming data into data stores and analytics tools. It can capture, transform, and load streaming data into Amazon S3, Amazon Redshift, Amazon OpenSearch Service, and Splunk, enabling near real-time analytics.

It is a fully managed service that automatically scales to match the throughput of your data and requires no ongoing administration. It can also batch, compress, and encrypt the data before loading it.

**Why other options are incorrect:**
- **Option A** is incorrect because DynamoDB Streams captures changes to DynamoDB tables, not for loading streaming data to S3.
- **Option B** is incorrect because SQS is a message queuing service, not capable of transforming and loading data.
- **Option C** is incorrect because Redshift is for data warehousing, not for streaming data ingestion.

## References
- https://aws.amazon.com/firehose/
- https://aws.amazon.com/kinesis/data-streams/faqs/
- https://tutorialsdojo.com/amazon-kinesis/
